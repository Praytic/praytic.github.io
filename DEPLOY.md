### Deployment Steps
<sub>Edit 06.07.2016</sub>

---

1. Compile the whole `_harp` directory into `public` one with harp compiler.
```
cd _harp
harp compile --output ../public
```
2. Commit changes in `dev` branch as release changes and push separate public directory into `master` branch.
```
git add -A
git commit -m "Release ..."
git push
```