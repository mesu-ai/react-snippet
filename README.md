#Reusable react snippet

##file download snippet

```
const downloadFileFromURL = (url = '', filename = 'Authorization Sample') => {
    fetch(url)
      .then((response) => response.blob())
      .then((blob) => {
        const link = document.createElement('a');
        link.href = URL.createObjectURL(blob);
        link.download = filename;
        link.click();
      })
      .catch(console.error);
  };

```