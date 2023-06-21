##### TOOLS
````
https://github.com/swisskyrepo/GraphQLmap
````
##### CSRF not protected while creating mutuations
send the GET request and check if csrf protection is enabled in for this request
````
/api/graphql?query=mutation CreateSnippet($input: CreateSnippetInput!) {  createSnippet(input: $input) {    errors    snippet {      webUrl      __typename    }    needsCaptchaResponse    captchaSiteKey    __typename  }}&variables={"input":{"title":"Tesssst Snippet","description":"Hello World","visibilityLevel":"public","blobActions":[{"action":"create","previousPath":"readme.md","content":"reading this.md","filePath":"readme.md"}],"uploadedFiles":[],"projectPath":""}}
````
##### Graphql introspection query visualizer
````
https://graphql-kit.com/graphql-voyager/
````
