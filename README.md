# zim-import-tomboy

Converts Tomboy notes to Zim notes preserving as much structure as is feasible.

Key features:

* accurately translates *most* Tomboy markup
* will fix links marked as "broken" if the target exists
* uses Zim-safe file names and adjusts links accordingly
* Zim-style markup in the Tomboy note is masked using zero width spaces
* Tomboy categories are mapped to Zim folders, with links adjusted accordingly
* Broken links can be optionally dropped


Markup notes:

* monospace blocks are converted to verbatim where possible
* size large/huge lines are converted to headings if possible
* datetime segments (a Tomboy plugin) are converted to italic
* bugzilla links (a Tomboy plugin) are correctly converted
* Zim does not provide a good way to escape its own markup syntax,
  so when such syntax occurs in the Tomboy note, it is obscured with
  zero width spaces (`\u200b`)



## Usage

Recommended invocation:

```
# zim-import-tomboy -o OUTPUTDIR
```

By default, the script will look for your existing Tomboy or Gnotes directory and
write the conversion to your current directory.
If you want finer grained control, see the options.


```
Usage: zim-import-tomboy [options]

Options:
  -h, --help            show this help message and exit
  -i INPUT, --input=INPUT
                        Input directory
  -o OUTPUT, --output=OUTPUT
                        Output directory
  --no-broken           Don't carry over broken links
  -f, --force           Overwrite output directory if present
```


## License

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.


## History

After using Tomboy for 13 years I decided to switch to Zim,
but I wanted to preserve my notes as accurately as possible.

Existing scripts to convert from Tomboy to Zim were helpful, but missed key details that I cared
about (e.g. nested lists, verbatim blocks, getting links right).

I started out trying to update the [tzim](https://github.com/osamuaoki/tzim|tzim) script, but
ended up rewriting everything several times over.

Some of the xml parsing was inspired by a [gist](https://gist.github.com/scribu/7442170) by scribu.
