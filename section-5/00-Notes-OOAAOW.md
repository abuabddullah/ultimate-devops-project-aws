# Install and Build Go for *src/product-catalog/README.md*
1. run the command:
   ```
   sudo apt install golang-go
   ```
2. check version of go
   ```
   go --version
   ```
3. clone the repo [https://github.com/abuabddullah/ultimate-devops-project-demo.git](https://github.com/abuabddullah/ultimate-devops-project-demo.git)
4. go to **src/product-catalog/README.md** folder of **ultimate-devops-project-demo** project
5. set the env
   ```
   export PRODUCT_CATALOG_PORT=8088
   ```
7. build the prject
   ```
   go build -o product-catalog . 
   ```
8. 
