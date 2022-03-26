# webSights
Well-labeled files & regexes to search for when performing reconnaissance against websites. webSights aims to provide clear, reliable cheatsheets for files/data/etc. that usually shouldn't be published to public webservers, such as `.git` directories, backend packaging information, open directories, and more.

## Bishop
**Requires: 'path' *and* 'validation'**

If you want to passively scan a subset of the websites you visit (which you are authorized to perform security testing against; such as penetration testing engagements) for exposed, problematic information, you can use the fantastically straightforward [bishop](https://github.com/jkingsman/bishop) extension from [Jack Kingsman](http://jacksbrain.com). All you need to do is install his Chrome extension, and either load in his predefined demos or one of the lists from our `bishop/` directory. I'd recommend the `bishop/version_control.json` list especially.

## Wordlists
**Requires: 'path'**

If you are looking to load these wordlists into your preferred spider, directory buster, etc., you'll probably want something out of the `wordlists/` directory. If there's anything in particular you're looking for, use one of the specialized ones, but if you don't care about making some noise and want the most coverage, `wordlists/all.txt` is a viable option.

## Development
Interested in contributing some nastygrams that you've seen people leave around or accidentally `rsync`'d to a server? There are two quick pointers before you do so. If you have any questions about the following, please open an issue!

### Structure
Each file to check is defined in YAML, has a few descriptive attributes, and is organized into folders by type (ex. package managers, version control, unconfigured applications). This has a number of benefits:

- You immediately know what has been found and why it is a finding.
- For tools that support it, you also get validation beyond "Wow, a 200! Time to throw an alert!"
- My life is 0.02% less frustrating to maintain.

### Contributing
Contributing is straightforward: create or append data to a YAML-formatted file in the most relevant `sources/<class_name>` folder (create a new class name if needed!) with the format:

```yaml
'Short title':
    description: 'A lengthier description so people know what has been found'
    path: 'OPTIONAL: The filename to look for, or the filename with a preceding path'
    validation: 'OPTIONAL: A string to match which confirms the finding'
```

Ensure it is named the path you want checked, and has a title, description for the finding, and validation regex. Then just run `compile.py`, add all the changed files, and submit a PR. Easy!