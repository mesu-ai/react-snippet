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

### handle outside click dropdown close

call from other components

const [isOpen,setIsOpen]=useState(false);
 const ref = useOutSide(() => setIsOpen(false));

```
 import { useEffect, useRef } from "react";

const useOutSideClick = (handleClose) => {
  const ref = useRef(null);

  useEffect(() => {
    const handleClickOutside = (event) => {
      if (ref.current && !ref.current.contains(event.target)) {
        // setIsOpen(false);
        handleClose();
        // console.log(ref);
      }
    };

    document.addEventListener('click', handleClickOutside, true);

    return () => {
      document.removeEventListener('click', handleClickOutside, true);
    };
  }, [handleClose]);

  return ref;
};

export default useOutSideClick;



```