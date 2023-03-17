# Technologies d'applications mobiles

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les différences entre les webapps, les applications hybrides et natives  ✔️
- le fonctionnement d'une app React Native, ce qui sera en réalité produit et installé sur le téléphone de mes utilisateur·rices, comment le JS arrive à communiquer avec le natif  ✔️
- quelles sont les différentes technologies (frameworks) existantes pour développer des apps mobiles  ✔️
- quels sont les principaux points d'attention entre le développement d'une app mobile ou desktop  ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```tsx

// le header d'une application
type Props = {
	title?: string
	titleVariant?: TextVariants
	noBack?: boolean
	onPressBack?: () => void
	action?: ReactNode,
	actionStyle?: ViewStyle,
	wrapperStyle?: ViewStyle,
	avatar?: EveAvatarProps,
	bgImg?: ImageSourcePropType,
}

const NavigationHeader: React.FC<Props> = ({ wrapperStyle, title, titleVariant, noBack, onPressBack, action, actionStyle, avatar, bgImg }) => {
	const theme = useTheme()

	const styles = useMemo(() => themedStyles(theme), [theme])

	const navigation = useNavigation()

	const _onPressBack = () => {
		if (noBack)
			return
		if (onPressBack)
			onPressBack()
		else
			navigation.goBack()
	}

	return <Box style={[styles.layout, wrapperStyle]} >
		{bgImg && <Box pos='absolute' style={[styles.backgroundImageContainer]}  >
			<ImageBackground source={bgImg} style={[styles.backgroundImage]} resizeMode='cover' />
			<Box pos='absolute' fullWidth h='100%'>
				<EveLinearGradient
					colors={[chroma(theme.colors.background!).alpha(0).hex(), chroma(theme.colors.background!).alpha(0.4).hex()]}
					start={{ x: 1, y: 0 }}
					end={{ x: 1, y: 1 }}
					style={{ height: '100%' }}
				/>
			</Box>
		</Box>}
		<TouchableOpacity style={styles.back} onPress={_onPressBack}>
			<EveIcon name="chevron-left" size={32} color={noBack ? 'transparent' : theme.colors.textPrimary} />
		</TouchableOpacity>
		{title &&
			<Box style={styles.title}>
				{avatar && <EveAvatar {...avatar} />}
				<EveText variant={titleVariant ?? "h1"} numberOfLines={1} fontSize={title?.length > 16 ? 18 : 28}>{title}</EveText>
			</Box>
		}
		<Box style={[styles.action, actionStyle]}>
			{action}
		</Box>
	</Box>
}

const themedStyles = (theme: Theme) => StyleSheet.create({
	layout: {
		width: "100%",
		flexDirection: 'row',
		alignItems: 'center',
		paddingHorizontal: 16,
		paddingTop: theme.safeArea.top + 24,
		paddingBottom: 24,
		backgroundColor: theme.colors.background
	},
	title: {
		alignSelf: "center",
		flex: 1,
		flexDirection: 'row',
		justifyContent: "center",
	},
	action: {
		width: 32,
		alignSelf: 'flex-end',
	},
	backgroundImageContainer: {
		borderBottomLeftRadius: 14,
		borderBottomEndRadius: 14,
		overflow: 'hidden',
	},
	backgroundImage: {
		width: theme.windowWidth,
		height: 80 + theme.safeArea.top,
	},
	back: {
		width: 32,

	},
})


```
### Utilisation en production si applicable ✔️


Description : Eve App

### Utilisation en environement professionnel ✔️

Description : Eve App

## 🌐 J'utilise des ressources

- [Doc React Native](https://reactnative.dev/docs/components-and-apis)
- [Doc React Navigation](https://reactnavigation.org/docs/getting-started)
- [chakra-ui pour le style](https://chakra-ui.com/docs/getting-started)


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
- J'ai ecrit un [article](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
