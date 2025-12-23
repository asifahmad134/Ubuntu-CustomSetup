## The process for installing Ruby 3.3.8 using mise

1. Install Dependencies

```
sudo nala update
sudo nala install build-essential rustc libssl-dev libyaml-dev zlib1g-dev libgmp-dev -y
```

2. Install Ruby 3.3.8 /Set Ruby Version (Global or Local)

```
mise install ruby@3.3.8
mise use --global ruby@3.3.8
mise use ruby@3.3.8
```

3. Verify

```
ruby -v
gem -v
gem update --system
gem install rails
// in working project dirs with gem file
bundle install
rails s
```
