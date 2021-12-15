# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

> 👌 Validation par le formateur

## 🎓 J'ai compris et je peux expliquer

- les différences et points communs entre du code react et du code react native ✔️
- ce que devient et comment est interprêté le code javascript dans une application react native ✔️
- les avantages et inconvénients de react native ✔️
- la différence entre react native et expo ✔️
- les principales briques qui composent react native (core components) ✔️
- comment écrire du style en react native ✔️
- comment est géré le layout en react native ✔️

## 💻 J'utilise

### Un exemple personnel commenté

```javascript
import * as FileSystem from "expo-file-system";

// FileStystem permet de lire des photos

import React, { useEffect, useState } from "react";
import { StyleSheet, Image, FlatList, Button } from "react-native";
import axios from "axios";

export default function ImagesScreen() {
  const [imagesURI, setImagesURI] = useState([]);
  useEffect(() => {
    (async () => {
      images = await FileSystem.readDirectoryAsync(
        FileSystem.cacheDirectory + "ImageManipulator"
      );
      setImagesURI(images);
    })();
  }, []);
  return imagesURI.length > 0 ? (
    <FlatList
      data={imagesURI}
      keyExtractor={(imageURI) => imageURI}
      renderItem={(itemData) => {
        console.log("item", itemData);
        return (
          <>
            <Image
              style={styles.image}
              source={{
                uri:
                  FileSystem.cacheDirectory +
                  "ImageManipulator/" +
                  itemData.item,
              }}
            />
            <Button
              title="upload"
              onPress={async () => {
                // onPress permet de déclencher une action lorsque l'utilisateur appui dessus

                const data = new FormData();
                data.append("fileData", {
                  uri:
                    FileSystem.cacheDirectory +
                    "ImageManipulator/" +
                    itemData.item,
                  type: "image/jpeg",
                  name: itemData.item,
                });
                let serverResponse;
                try {
                  serverResponse = await axios({
                    method: "post",
                    url: "https://jouvenciacrew.dev/upload",
                    data,
                    headers: { "Content-Type": "multipart/form-data" },
                  });

                  // Ici on fetch avec axios, pour poster une image

                  if (serverResponse.status === 200) {
                    alert("Uploaded");
                  }

                  // Si succès l'utilisateur est alerté
                } catch (err) {
                  console.log(err);
                  alert("Error");
                }
              }}
            />
          </>
        );
      }}
    />
  ) : null;
}

const styles = StyleSheet.create({
  image: {
    resizeMode: "cover",
    height: 500,
  },
});
```

### Utilisation dans un projet ❌

[lien github](...)

Description :

### Utilisation en production si applicable❌

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌

Description: ne connais pas du tout

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
