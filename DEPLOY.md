### Deployment Steps
<sup>Edit 11.09.2016</sup>

---

Compile contents of `_harp` directory into `public` directory with harp compiler.
```
cd _harp
harp compile --output ../public
```
Commit changes in `dev` branch and push `public` directory into `master` branch.
```
git add -A
git commit -m "Release ..."
git push
```
