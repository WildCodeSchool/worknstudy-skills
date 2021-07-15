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
- comment écrire du style en react native  ✔️
- comment est géré le layout en react native ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```tsx
//un composant 
type Props = {
	onPressImage: (image: MediaFile) => void
	image: MediaFile
}

//Component GalleryItem to render images coming from back (MediaFile)
const GalleryRemoteImage: React.FC<Props> = ({ onPressImage, image }) => {
	const theme = useTheme()
	const styles = useMemo(() => themedStyles(theme), [theme])
	const [checked, setChecked] = useState(false)

	const availableWidth = theme.windowWidth - 64
	const imageSize = availableWidth / 4

	const onPress = () => {
		setChecked(!checked)
		onPressImage(image)
	}

	return <Box p={4}>
		<TouchableOpacity onPress={onPress}>
			<EveCheck style={{ position: "absolute", zIndex: 9, top: 6, right: 6 }} checked={checked} />
			<EveCachedImage noCache style={{ width: imageSize, height: imageSize, borderRadius: 14 }} uri={image.file ? image.file : ""} />
		</TouchableOpacity>
	</Box>
}

const themedStyles = (theme: Theme) => StyleSheet.create({

})


export default React.memo(GalleryRemoteImage)

```

### Utilisation dans un projet ✔️


Description : uniquement effectué en entreprise

### Utilisation en production si applicable ✔️

Description : Eve app (bientôt disponible)

### Utilisation en environement professionnel ✔️

Description : Eve app (bientôt disponible)

## 🌐 J'utilise des ressources

- [Doc React Native](https://reactnative.dev/docs/components-and-apis)
- [Doc React Navigation](https://reactnavigation.org/docs/getting-started)
### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
