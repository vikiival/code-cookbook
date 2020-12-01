# Create release

This uses the [Create Release](https://github.com/actions/create-release) action and is based on the doc's example.

- `main.yml`
    ```yaml
    name: Create Release
    
    on:
      push:
        tags:
          - 'v*'

    jobs:
      build:
        name: Create Release
        runs-on: ubuntu-latest
        
        steps:
          - name: Checkout code
            uses: actions/checkout@v2
            
          - name: Create Release
            id: create_release
            uses: actions/create-release@v1
            env:
              GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
            with:
              tag_name: ${{ github.ref }}
              release_name: Release ${{ github.ref }}
              body: |
                Changes in this Release
                - First Change
                - Second Change
              draft: false
              prerelease: false
    ```