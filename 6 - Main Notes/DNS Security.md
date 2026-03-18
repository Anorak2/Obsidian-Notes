
2026-03-05

Tags: [[Networking and Network Security]]
# DNS Security
As a review we need DNS to resolve hostnames (`myweb.com`) to individual servers (ex 192.168.1.17), for more see [[DNS Servers]] and [[DNS Queries]]. 

## DNS Cache Poisoning
DNS relies heavily on caching for efficiency since the full trip is not necessary if we save an authoritative answer for a given name in a local cache. Importantly we also shouldn't cache our result forever since things change, thus we add a TTL so it expires.

### On-path
Each DNS query has a unique 16 bit (65536 possible values) query ID, and if an attacker knows/guesses the the query ID (also known as `TXID`) it can forge responses. Since DNS requests and responses are not otherwise authenticated by default, this is problematic since many applications trust DNS resolutions. This leads to a simple and effective attack:
```
1. Wait for Alice to send DNS request to name server
2. Intercept request
3. Quickly insert a fake response
4. Later, redirect traffic to attacker’s own malicious site
```
This works better the closer the attacker is to the target since have introduced a [[Race Conditions|Race Condition]], but the attacker is favored since they don't have to do any actual resolution.
### Off-path
If we aren't able to intercept the DNS request then we have to get more creative. Many old name servers increase IDs or use some predictable algorithms to generate ID meaning we can use that as a baseline.
```
1. Craft the DNS request
2. Flood the victim name server with forged replies
3. If the right reply came later than the forged one, it will be discarded
```
**Solution:** Randomize the transaction ID for every query
### Kaminsky Attack
This attack, described in [CVE-2008-1447](https://nvd.nist.gov/vuln/detail/CVE-2008-1447), targets a particular recursive name server and hijacks the entire `ns` of the victim host. Since we are being proactive the likelihood of succeeding is significantly better over a reactive off-path attack. 
```
1. Attacker requests a random name in the target domain (that is essentially guaranteed not be in the cache)
2. Attacker sends many forged packets to the victim to delegate to another name server
3. If we beat the real name servers response by guessing the TXID, profit
	if not then go back to step 1 until successful
```
## DNSSEC
While we could try to mitigate hijacking attacks by increasing the entropy through randomization the root problem is still possible, thus DNSSEC is based on cryptography.

DNSSEC supports authentication through public key infrastructure (PKI) allowing each domain to sign it's zone with a private key. Public keys published via a `DNSKEY` record, binding the public key with a domain. This allows for authentication between servers and also authenticates DNS data: content, existence or non-existence.

| Record                    | Description                          |
| ------------------------- | ------------------------------------ |
| RRSIG                     | Contains a cryptographic signature   |
| DNSKEY                    | Contains a public signing key        |
| DS                        | Contains the hash of a DNSKEY record |
| NSEC, NSEC3, CDNSKEY, CDS | ...                                  |

**DNSSEC Challenges:**
- Incremental deployability, can't just "switch on"
- Resource imbalances since some devices can’t afford real authentication
- Economic and cultural concerns since who gets to control the root keys? Also why secure DNS? Cost may not be justified in most environments.

**Problems:**
• DoS amplification/exhaustion attacks
• Delegation records may still be forged

DNSSEC will be deployed, but it is unclear whether it will be used appropriately/widely. It's management should also be automated and audited.
# References
- [[DNS Servers]]
- [[DNS Queries]]