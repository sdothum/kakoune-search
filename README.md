# kakoune-search (and replace)

**NOTE:** This is a fork of kakoune-find and has been modified to:

1. present the search results in a 2 column format: buffer:line:column (right
justified) and matching text (left justified)
2. highlight the buffer:line:column as a single highlight block
3. allow setting the highlight face (search_coordinate -- default:
SecondarySelect) for the buffer:line:column block
and (search_select -- default: comment) pattern match
4. adds an additional command "search-view" to restore the search pattern
(highlight) of the *search* buffer (useful if chained to commands that reswitch to
the *search* buffer if your workflow switches out of that view -- WARNING: changes
made outside of the view will not be reflected in the view and the search
should be reinitiated to refresh the view)

[kakoune](http://kakoune.org) plugin to search for a pattern in all open buffers, and optionally replace it. Works similarly to `grep.kak`, but does not operate on files.

[![demo](https://asciinema.org/a/160951.png)](https://asciinema.org/a/160951)

NOTE: this is the original demo and does not reflect the columnar presentation
kakoune-search provides.


## Setup

Add `search.kak` to your autoload dir: `~/.config/kak/autoload/`, or source it manually.

## Usage

### Finding

Call the `search` command. You can specify the pattern as the first argument, otherwise the content of the main selection will be used. From the
`*search*` buffer you can jump to the actual match using `<ret>`.

### Replacing

Replacing is done from the `*search*` buffer. Write directly there the changes that you want to make. Then, call
`search-apply-changes`: the changes will be applied back to their respective buffers. Any lines that were not modified are simply ignored.

By default, this command only works on open buffers. However, you can specify `-force` to make kakoune temporarily open the file to write the change.

Since the format is the same as [grep.kak's](https://github.com/mawww/kakoune/blob/master/rc/tools/grep.kak), this command can just as well be used from a `*grep*` buffer. Any line that doesn't follow the `<file>:<line>:<column>:<content>` pattern is simply ignored. 

## License

Unlicense
