# drone/drone-ui

<https://github.com/drone/drone-ui>

```bash
git remote add upstream git@github.com:drone/drone-ui.git

git fetch upstream

git merge v2.9.1
```

## debug

```bash
# nodejs 14

# 0. **Import dependencies from package-lock.json
yarn import

# 1. **Install dependencies**
yarn

# 2. **Copy .env.example and rename it into .env**
cp .env.example .env.development.local

# 3. **Fill required variables. For example:**
REACT_APP_DRONE_SERVER=https://drone.company.com
REACT_APP_DRONE_TOKEN=<your_drone_token>

# Run the app
export PUBLIC_URL=/awecloud/devops
yarn start
```

## edit

<!-- 0001-add-user-alias.patch -->
为用户User增加Alias昵称显示

## build

```bash
# apply patch
git apply .beagle/0001-add-user-alias.patch
git apply .beagle/0002-awecloud-devops.patch

## build nodejs
export PUBLIC_URL=/awecloud/devops
yarn build

## install togo
go install github.com/bradrydzewski/togo@latest

## go generate
go generate dist/dist.go
```

## publish

```bash
# 新建一个Tag
git tag v2.9.1-beagle.8

# 推送一个Tag ，-f 强制更新
git push -f origin v2.9.1-beagle.8

# 删除本地Tag
git tag -d v2.9.1-beagle.8
```