[![42 Profile Card](https://1337-readme.vercel.app/api/profile?cursus=42cursus&dark=true&email=hide&leet_logo=hide&login=fharing)](https://profile.intra.42.fr/users/fharing)

# Visit https://github.com/lowlighter/metrics/blob/master/action.yml for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: fharing
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Europe/Berlin
          plugin_languages: yes
          plugin_languages_colors: github
          plugin_languages_limit: 8
          plugin_languages_recent_days: 14
          plugin_languages_recent_load: 300
          plugin_languages_sections: most-used
          plugin_languages_threshold: 0%