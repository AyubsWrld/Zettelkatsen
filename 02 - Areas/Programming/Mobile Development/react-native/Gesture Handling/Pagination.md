```javascript
import React, { useState, useRef } from 'react';
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View, TouchableOpacity, ScrollView, Dimensions } from 'react-native';

const { width: SCREEN_WIDTH } = Dimensions.get('window');

export default function App() {
  const [currentPage, setCurrentPage] = useState(0);
  const scrollViewRef = useRef(null);

  const content = [
    {
      subtitle: "Clear Learning, Achieved Simply",
      title: "Effortless Tutor Booking Anytime, Anywhere.",
    },
    {
      subtitle: "Personalized Learning",
      title: "Find the Perfect Tutor for Your Needs",
    },
    {
      subtitle: "Flexible Scheduling",
      title: "Book Sessions at Your Convenience",
    }
  ];

  const handleScroll = (event) => {
    const offsetX = event.nativeEvent.contentOffset.x;
    const page = Math.round(offsetX / SCREEN_WIDTH);
    if (page !== currentPage) {
      setCurrentPage(page);
    }
  };

  return (
    <View style={styles.container}>
      <StatusBar style="auto" />
      <View style={styles.imageContainer}>
        {/* Placeholder for image */}
      </View>
      <ScrollView
        ref={scrollViewRef}
        horizontal
        pagingEnabled
        showsHorizontalScrollIndicator={false}
        onScroll={handleScroll}
        scrollEventThrottle={16}
        style={styles.scrollView}
      >
        {content.map((item, index) => (
          <View key={index} style={styles.page}>
            <View style={styles.TextContainer}>
              <Text style={styles.subtitle}>{item.subtitle}</Text>
              <Text style={styles.title}>{item.title}</Text>
            </View>
          </View>
        ))}
      </ScrollView>
      <View style={styles.pagination}>
        {content.map((_, index) => (
          <View
            key={index}
            style={[
              styles.circle,
              index === currentPage && styles.activeCircle
            ]}
          />
        ))}
      </View>
      <TouchableOpacity style={styles.button}>
        <Text style={styles.buttonText}>Get started</Text>
      </TouchableOpacity>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'space-between',
    paddingTop: 60,
    paddingBottom: 40,
  },
  imageContainer: {
    backgroundColor: '#f0f0f0', // Placeholder color
    height: 430,
    width: 345,
    borderRadius: 20,
    marginBottom: 20,
  },
  scrollView: {
    width: SCREEN_WIDTH,
  },
  page: {
    width: SCREEN_WIDTH,
    alignItems: 'center',
    justifyContent: 'center',
  },
  pagination: {
    flexDirection: 'row',
    justifyContent: 'center',
    alignItems: 'center',
    marginBottom: 20,
  },
  circle: {
    height: 12,
    width: 12,
    borderRadius: 6,
    backgroundColor: '#D1D5DB',
    marginHorizontal: 6,
  },
  activeCircle: {
    backgroundColor: '#4B5563',
    width: 24,
    borderRadius: 12,
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold',
    textAlign: 'center',
    marginBottom: 10,
  },
  subtitle: {
    fontSize: 16,
    textAlign: 'center',
    color: '#4B5563',
  },
  button: {
    backgroundColor: '#6D6D6D',
    paddingVertical: 15,
    width: '90%',
    borderRadius: 25,
    alignItems: 'center',
  },
  buttonText: {
    color: '#fff',
    fontSize: 18,
    fontWeight: 'bold',
  },
  TextContainer: {
    paddingHorizontal: 20,
    marginBottom: 32,
    gap: 8,
    alignItems: 'center',
  },
});


```
____
Tags : #programming #school #software-design #lucidity