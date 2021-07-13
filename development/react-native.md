# React Native
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

### Un exemple personnel commenté ✔️
Ecran de login
```javascript
export default function LoginScreen({ navigation }: LoginScreenProps) {
  // context à mémoriser
  const { signIn } = React.useContext(AuthContext);
  // mutation
  const [loginUser, { data, error }] = useMutation(LOGIN_USER, {
    onCompleted: async (data) => {
      const token = data?.loginUser?.token;
      if (token) {
        // stocke le token
        await SecureStore.setItemAsync("userToken", data.loginUser.token);
        // met en place le context
        signIn();
        // redirection
        navigation.navigate("LamasToolsScreen");
      }
    },
    errorPolicy: "all",
  });

  return (
    <LinearGradient
      style={styles.container}
      colors={["#00396A", "#0371c8", "#00396A"]}
      start={{ x: 0.2, y: 0 }}
      end={{ x: 0.7, y: 0.5 }}
    >
      <Image
        source={require("../assets/images/logowhite.png")}
        style={styles.logo}
      />
      <View style={styles.containerLogin}>
        <Text style={styles.title}>Retrouve tes Lamas Tools </Text>
        {/* formulaire de login */}  
        <Formik
          initialValues={{ email: "", password: "" }}
          onSubmit={(values) => loginUser({ variables: { ...values } })}  {/* appel de la mutation */} 
          validationSchema={loginValidationSchema} {/* vérification de la validité des données */} 
        >
          {({
            handleChange,
            handleSubmit,
            values,
            errors,
            touched,
            isValid,
          }) => (
            <>
              <View style={styles.containerInput}> {/* équivalent à une div */} 
                <Input
                  placeholder="E-mail"
                  onChangeText={handleChange("email")}
                  value={values.email}
                  style={styles.input}
                  leftIcon={<Icon style={styles.icons} name="mail" size={18} />}
                />
                {errors.email && touched.email && (
                  <Text style={styles.errors}>{errors.email}</Text> {/* équivalent à un span*/} 
                )}
              </View>
              <View style={styles.containerInput}>
                <Input
                  placeholder="Mot de passe"
                  onChangeText={handleChange("password")}
                  value={values.password}
                  style={styles.input}
                  secureTextEntry
                  leftIcon={<Icon style={styles.icons} name="lock" size={18} />}
                />
                {errors.password && touched.password && (
                  <Text style={styles.errors}>{errors.password}</Text>
                )}
              </View>
              <Button
                title="Se connecter"
                onPress={() => handleSubmit()} {/* utilisation de onPress au lieu de onClick sur React */} 
                buttonStyle={styles.button}
              />
            </>
          )}
        </Formik>
      </View>
      <View style={styles.footer}>
        <Text style={styles.footertext}>
          Made with <IconAnt name="heart" size={18} color="red" /> by Lamas
        </Text>
      </View>
    </LinearGradient>
  );
}

// CSS React Native
const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: "center",
    backgroundColor: "#00396A",
    paddingTop: 70,
    justifyContent: "space-around",
  },
  containerLogin: {
    marginBottom: 100,
    borderRadius: 10,
    height: "auto",
    width: 350,
  },
  title: {
    fontSize: 20,
    fontWeight: "bold",
    color: "#00396A",
    textAlign: "center",
    paddingTop: 30,
    paddingBottom: 20,
  },
  containerInput: {
    paddingHorizontal: 25,
  },
  label: {
    color: "#00396A",
  },
  logo: {
    height: 200,
    resizeMode: "contain",
  },
  button: {
    width: 150,
    alignSelf: "center",
    marginTop: 20,
    backgroundColor: "#00396A",
    marginBottom: 40,
    borderRadius: 10,
  },
  input: {
    fontSize: 14,
  },
  errors: {
    color: "red",
    marginBottom: 8,
    marginLeft: 10,
  },
  icons: {
    color: "#00396A",
    paddingRight: 10,
  },
  footer: {
    flexDirection: "column",
    alignItems: "flex-end",
    alignContent: "flex-end",
    backgroundColor: "transparent",
  },
  footertext: {
    color: "white",
    alignSelf: "flex-end",
  },
});
```

### Utilisation dans un projet ✔️
[lien github du projet Lamas](https://github.com/WildCodeSchool/wns-2020-11-remote-1-lamas/tree/main/mobile)
Description : Création d'une interface mobile pour le projet Lamas.

### Utilisation en production si applicable ❌
### Utilisation en environement professionnel ❌

## 🌐 J'utilise des ressources
### [React Native](https://reactnative.dev)
- Documentation React Native
### [React Navigation](https://reactnavigation.org)
- Documentation pour le routing et la navigation de React Native
### [Quête de la Wild Code School](https://odyssey.wildcodeschool.com/quests/1532)
- Présentation de React Native
### [Expo](https://expo.io)
- Documentation sur l'outil qui facilite le développement d'une application React Native


## 🚧 Je franchis les obstacles
### Point de blocage ❌ 


## 📽️ J'en fais la démonstration
- J'ai ecrit une [fiche](https://docs.google.com/document/d/1pSOqaQuOkwhs65Cxlh1u7-jZUcEdoBjycLUgVSGrtBA/edit?usp=sharing)
