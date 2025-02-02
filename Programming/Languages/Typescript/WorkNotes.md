#### Interface

```Typescript
interface FileItem {
    name     :    string ; 
    isActive :    bool   ; 
 }

```

##### Interface Functions  

```Typescript
interface foo{
    bar : () => void ; 
 }

```

```typescript
const DrawerMenu: React.FC<{
  isVisible: boolean;
  translateX: Animated.Value;
  onClose: () => void;
}> = ({ isVisible, translateX, onClose }) => {
  const menuItems = [
    { icon: "timer-outline", label: "Recent" },
    { icon: "star-outline", label: "Starred" },
    { icon: "folder-outline", label: "Folders" },
    { icon: "trash-outline", label: "Trash" },
    { icon: "settings-outline", label: "Settings" },
    { icon: "help-circle-outline", label: "Help & Feedback" },
  ];

  return (
    <>
      {isVisible && (
        <TouchableWithoutFeedback onPress={onClose}>
          <Animated.View style={[styles.backdrop, { opacity: 0.5 }]} />
        </TouchableWithoutFeedback>
      )}
      <Animated.View
        style={[
          styles.drawer,
          {
            transform: [{ translateX }],
            display: isVisible ? "flex" : "none",
          },
        ]}>
        <SafeAreaView style={styles.drawerContent}>
          <Text style={styles.drawerTitle}>Graphite</Text>
          {menuItems.map((item, index) => (
            <TouchableOpacity key={index} style={styles.drawerItem}>
              <Ionicons
                name={item.icon as keyof (typeof Ionicons)["glyphMap"]}
                size={24}
                color="#4285f4"
              />
              <Text style={styles.drawerItemText}>{item.label}</Text>
            </TouchableOpacity>
          ))}
        </SafeAreaView>
      </Animated.View>
    </>
  );
};
```



import { View, Text, StyleSheet  , Button } from "react-native";



interface fileHandler {
  bar : () => void ; 
}

const handleAdd : fileHandler = { 
  bar : () => {
    console.log("Hello World") ; 
  }
}

export default function Expr() {
  return (
    <View style={styles.container}>
      <Text>EXPR SCREEN</Text>
      <Button onPress={handleAdd.bar} title="pressme">  </Button>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center",
  },
});
