### Deployment Steps
<sup>Edit 11.09.2016</sup>

---

Compile contents of `_harp` directory into `public` directory with harp compiler.
```
cd _harp
harp compile --output ../public
```
Copy changes from `public` directory to `master` branch root directory.
```
git checkout master
git read-tree dev:public
```
Commit new changes and push them to the remote repository.
```
git commit -m "Release 'blah-blah' page"
git push origin master
```
