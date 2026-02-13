# Travel Diary App 

**A simple travel diary Flutter app to capture and revisit your travel memories.**

---

## Project summary

This project is a Flutter mobile app that lets users record travel journals with title, notes, date, location (picked on a map), images, and a rating. It uses Firebase for authentication and Firestore to store journal entries.

## Key features

- Email/password authentication (Firebase Auth)
- Optional biometric login via `local_auth`
- Add/edit/delete travel journal entries (title, notes, date, rating)
- Pick location on an interactive map (OpenStreetMap via `flutter_map` + Nominatim reverse geocoding)
- Add photos via camera/gallery (stores local image path) and simple image controls
- Search and list your journal entries

## Tech stack

| Component | Technology |
|---|---|
| Framework | Flutter (Dart) |
| State & UI | Material + google_fonts + flutter_animate |
| Maps & Location | flutter_map (OpenStreetMap), latlong2, geolocator |
| Storage & Auth | Cloud Firestore, Firebase Auth, Firebase Core |
| Local auth | local_auth (biometrics) |
| Media | image_picker, image_cropper |
| HTTP | http |

## Project structure (important files)

- `lib/main.dart` — app entry / welcome screen
- `lib/journal.dart` — authentication screen and biometric flow
- `lib/menu.dart` — journal list (home) and search
- `lib/entries.dart` — Add new journal/form & saving to Firestore
- `lib/location_picker.dart` — map UI and Nominatim search/reverse geocoding
- `lib/JournalDetailsPage.dart` — journal detail view, edit & delete
- `pubspec.yaml` — dependencies

---

## Development setup

Prerequisites:
- Flutter SDK (see https://flutter.dev/docs/get-started/install)
- Android/iOS toolchains set up for your target device
- Git & gh (GitHub CLI) configured with your account

Quick start:

1. Clone the repository:

```bash
git clone https://github.com/MalimGunung/travel-diary-app.git
cd travel-diary-app
```

2. Install dependencies:

```bash
flutter pub get
```

3. Configure Firebase:
- Create a Firebase project and enable **Authentication** (Email/Password) and **Cloud Firestore**.
- Download `google-services.json` and place it in `android/app/`.
- Download `GoogleService-Info.plist` and place it in `ios/Runner/`.

> Important: These files contain credentials — do NOT commit them to the repo. They are included in `.gitignore`.

4. Run the app:

```bash
flutter run -d <device-id>
```

---

## Notes on security & data

- The app currently stores selected image file paths locally (`imagePath` in Firestore). For multi-device access, consider uploading images to Firebase Storage and storing download URLs instead.
- Ensure Firestore Security Rules are configured to restrict access to authenticated users and per-user data (not shipped in this repo).

## Tests & CI

- There are no unit/widget tests yet. Recommended next steps:
  - Add `flutter_test` unit and widget tests for `AddJournalPage` and `JournalHomePage`.
  - Add GitHub Actions workflow to run `flutter analyze` and `flutter test` on PRs.

---


