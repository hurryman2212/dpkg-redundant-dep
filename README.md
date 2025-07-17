# dpkg‑redundant‑dep

dpkg-redundant-dep is a python command‑line tool that inspects installed Debian packages for redundant alternative dependencies—cases where two or more packages from the same “or” group are simultaneously installed.

## Why?

While `apt autoremove` and `apt autopurge` efficiently clean up truly unused packages, they don’t resolve cases where two or more alternatives from the same “or” group remain installed. Because the package manager can’t know which variant you prefer, it leaves all of them in place. This tool identifies every such redundant dependency group on your system and shows which alternatives are installed—so you can decide and remove the extras yourself.

## Usage

```bash
# Scan all installed packages
./dpkg-redundant-dep

# Scan only 'inxi' and its dependency groups
./dpkg-redundant-dep inxi
```

Sample output when running `dpkg-redundant-dep inxi`:

```
Package: inxi
  Installed: iproute2 | net-tools
  Installed: curl | wget
```
