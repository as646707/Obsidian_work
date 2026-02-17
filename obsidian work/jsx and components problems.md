hello this is my learning blog or whatever you wanna call it about problems and their solutions--
```
import React from 'react';
import { Text } from 'react-native';

const getFullName = (
  firstName: string,
  secondName: string,
  thirdName: string,
) => {
  return (firstName + ' ' + secondName + thirdName);   
};

const Cat = () => {
  return <Text>Hello, I am {getFullName('Rum', 'Tum', 'Tugger')}!</Text>;
};

export default Cat;
```
can you tell me what is wrong here ? 
