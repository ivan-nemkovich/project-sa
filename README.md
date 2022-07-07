# project-sa
Final project for it-academy
## add to workflow
```yml
- name: Helm tool installer
  uses: Azure/setup-helm@v3
  
- name: Helm Package
  run: |
    helm package chart/wp_project --version=${{ steps.tag.outputs.tag }} --app-version=${{ steps.tag.outputs.tag }}
    helm repo index --url https://ivan-nemkovich.github.io/project-sa/ --merge index.yaml .
    
- name: Commit changes
  run: |
    git config user.name github-actions
    git config user.email github-actions@github.com
    git add .
    git commit -m "generated"
    git push
