---
title: Author Intrusion
---

[Author Intrusion](https://authorintrusion.com/) is a set of libraries and tools designed to assist a writer in creating novels and stories. There are already hundreds, if not thousands, of word processors out there, but these tools are designed to work with other editors without limiting the writer to a specific platform, interface, or even operating systems.

There is no user interface for Author Intrusion, only configuration files. This works like other development project files such as `package.json` or `project.vcproj`. This file is tracked like any other text file, which makes it suited for working with source control systems.

# Mailing Lists and Forums

The forum for Author Intrusion can be found at [discuss.moonfire.us](http://discuss.moonfire.us/c/mfgames/author-intrusion). Various announcements, questions, and the like can be asked there. You can also subscribe to the forum in RSS/Atom or email.

# Development

Author Intrusion is in active development, but has not reached the "1.0.0" release. This means that the format of the files, how it works, or even how it is installed may change from day to day. The changes will be posted along with updated documentation when these elements will change. If it gets too confusing, please ask in the discussion forum.

# Getting Started

Because Author Intrusion is currently in development, there is no unified installer or easy setup. Instead, there are a set of directions These directions assume a Linux platform with Atom and Node JS installed.

See [this script](scripts/develop-author-intrusion) for basic steps for setting up the packages.

# Project File

In Atom, this will install the package which will automatically run when you edit or open a Markdown file. However, if there is no `project.aipy`, then nothing will happen. To use the features, create a `project.aipy` either in the same directory as the Markdown file or in a directory above it.

What to put in the file is more flexible and will change over time. For starters, use something like this inside `project.aipy`.

    {
        "name": "Sand and Blood",
        "analysis": [
            {
                "name": "split",
                "plugin": "node-author-intrusion-split"
            },
            {
                "name": "pos",
                "plugin": "node-author-intrusion-pos-tagger"
            },
            { 
                "name": "echoes",
                "plugin": "node-author-intrusion-echo",
                "options": {
                    "condition": [
                        {
                            "warning": 2500,
                            "error": 5000,
                            "field": "normalized",
                            "filter": {
                                "field": "normalized",
                                "search": "(he|she|it|his|her|hers|its)",
                                "type": "regex"
                            },
                            "score": [0.0, 0.0, 1.0]
                        }
                    ],
                    "range": 57,
                    "scope": "document"
                }
            }
        ]
    }
