
[[meta notes]]
```dataviewjs
let totalLines = 0;

// Collect all pages (files) in the vault, but only include files from certain folders
let files = dv.pages().file.filter(f => f.path.includes("6 - Main Notes/") || f.path.includes("Programming/") || f.path.includes("Math/")).map(f => f.path);

Promise.all(
    files.map(async path => {
        const content = await app.vault.read(app.vault.getAbstractFileByPath(path));
        return content.split("\n").length;
    })
).then(linesCounts => {
    totalLines = linesCounts.reduce((a, b) => a + b, 0); // Sum up all line counts
    dv.paragraph(`**Total lines in selected folders:** ${totalLines}`);
});

let totalWords = 0;

Promise.all(
    files.map(async path => {
        const content = await app.vault.read(app.vault.getAbstractFileByPath(path));
        return content.split(/\s+/).filter(word => word.length > 0).length; // Split into words and filter out empty strings
    })
).then(wordCounts => {
    totalWords = wordCounts.reduce((a, b) => a + b, 0); // Sum up all word counts
    dv.paragraph(`**Total words in selected folders:** ${totalWords}`);
});

let fileWordCounts = [];

Promise.all(
    files.map(async path => {
        const content = await app.vault.read(app.vault.getAbstractFileByPath(path));
        const wordCount = content.split(/\s+/).filter(word => word.length > 0).length; // Count words
        fileWordCounts.push({ file: path, words: wordCount });
    })
).then(() => {
    // Sort files by word count in descending order
    fileWordCounts.sort((a, b) => b.words - a.words);

    // Calculate the average word count
    const totalWords = fileWordCounts.reduce((sum, f) => sum + f.words, 0);
    const averageWords = totalWords / fileWordCounts.length || 0;

    // Display the average
    dv.paragraph(`**Average word count per file in selected folders:** ${averageWords.toFixed(2)}`);

    // Create the table
    dv.table(
        ["File Name", "Word Count"],
        fileWordCounts.map(f => [f.file, f.words])
    );
});

```
