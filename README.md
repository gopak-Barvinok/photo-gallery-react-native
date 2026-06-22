[README.md](https://github.com/user-attachments/files/29219473/README.md)
# 📸 Photo Gallery (React Native + Expo)

A simple mobile gallery app built with **React Native** and **Expo** that fetches photos from the public [Picsum Photos](https://picsum.photos/) API and displays them as an infinitely-scrolling grid with paginated loading.

## ✨ Features

- 🖼 Photos displayed in a 3-column grid
- ♾ Infinite scroll / pagination — new photos load automatically when the user reaches the end of the list
- ⏳ Loading indicator while fetching data
- ⚠️ Error handling for failed API requests
- 🌐 Cross-platform: iOS, Android, and Web (thanks to Expo)

## 🛠 Tech Stack

| Technology | Purpose |
|---|---|
| [React](https://react.dev/) 18 | UI library |
| [React Native](https://reactnative.dev/) 0.72 | Running the React app on mobile platforms |
| [Expo](https://expo.dev/) ~49 | Development, build, and run tooling |
| `useReducer` / `useCallback` (React Hooks) | Managing photo-loading state |
| [Picsum Photos API](https://picsum.photos/) | Image source |

## 📁 Project Structure

```
photo-gallery-react-native/
├── api/
│   └── picsum.js          # Requests to the Picsum Photos API
├── components/
│   └── PhotoGrid.js       # Photo grid component (FlatList)
├── reducers/
│   └── photos.js          # Reducer + action creators for photo state
├── assets/                # Icons, splash screen, etc.
├── App.js                 # App entry point
├── app.json               # Expo configuration
└── package.json
```

### How It Works

1. On mount, `App.js` calls `getList(nextPage)` from `api/picsum.js`, which hits the `https://picsum.photos/v2/list?page=...` endpoint.
2. The fetched photos and the loading/error state are managed by a `reducer` (`reducers/photos.js`) with three action types: `LOADING`, `SUCCESS`, `FAILURE`.
3. The list of photos is passed to the `PhotoGrid` component, which renders it as a grid via `FlatList` (`numColumns`), requesting the next page (`onEndReached`) once the user scrolls to the end.
4. Each image URL is built by the `formatPhotoUri(id, width, height)` function, which scales the image to fit the screen width.

## 🚀 Installation and Setup

### Requirements

- [Node.js](https://nodejs.org/)
- [Yarn](https://yarnpkg.com/) (the repo includes a `yarn.lock`) or npm
- [Expo Go](https://expo.dev/client) app on your phone (for testing on a physical device) or an iOS/Android emulator

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/gopak-Barvinok/photo-gallery-react-native.git
cd photo-gallery-react-native

# 2. Install dependencies
yarn install
# or
npm install

# 3. Start the project
yarn start
# or
npm start
```

Once started, Expo will open the Dev Tools in your browser, where you can scan the QR code with the Expo Go app or launch an emulator.

### Running on a Specific Platform

```bash
yarn android   # run on Android
yarn ios       # run on iOS
yarn web       # run in a browser
```

## 📦 Dependencies

```json
{
  "expo": "~49.0.15",
  "expo-status-bar": "~1.6.0",
  "react": "18.2.0",
  "react-dom": "18.2.0",
  "react-native": "0.72.6",
  "react-native-web": "~0.19.6",
  "@expo/webpack-config": "^19.0.0"
}
```

## 📝 License

No license is specified in the repository. If you plan to use this project commercially or as open source, it's recommended to check with the author or add a `LICENSE` file.

## 👤 Author

[gopak-Barvinok](https://github.com/gopak-Barvinok)
