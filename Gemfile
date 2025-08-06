source "https://rubygems.org"

# 核心Jekyll依赖（指定兼容版本）
gem "jekyll", "~> 3.9.5"  # 与你当前使用的版本匹配

# 本地安装Minima主题（避免远程加载问题）
gem "minima", "~> 3.0"  # 明确指定v3.x版本

# 可选：常用插件（根据需要添加）
gem "jekyll-feed", "~> 0.12"  # RSS订阅功能（Minima默认依赖）
gem "jekyll-seo-tag", "~> 2.8"  # SEO优化标签

# 开发环境依赖（可选）
group :development do
  gem "jekyll-watch", "~> 2.2"  # 自动监测文件变化
  gem "wdm", "~> 0.1.1" if Gem.win_platform?  # Windows系统文件监测
end

# 解决Faraday警告的依赖
gem "faraday-retry", "~> 2.2"
