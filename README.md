# google-books-android-viewer

Android application that scrolls over Google Books, displaying cover images and titles.

# Description

The app uses Google Books API to scroll over the list of content that is returned as search result. It consists of two screens (fragments). The list screen one allows to scroll over search results, showing only cover thumb image, header, author and page count. The details screen that opens after tapping anywhere on the book item reveals more information about the particular book. Use the back button for returning back to the list.

If you just want quick preview, the Android app is available at https://play.google.com/store/apps/details?id=com.ames.books&rdid=com.ames.books

# Architecture

To only app activity controls the two fragments (list and details screens). 

## List 
List is implemented on the top of RecyclerView and features 'endless scrolling' (new items are fetched automatically as you scroll down). Only 10 items are fetched in advance, and only fields used in the list are requested.  The list uses Picasso for image loading and caching. Queries to fetch more items are sent as required, taking care to partition them so that ranges requested by different queries do not overlap.

Behind the standard RecyclerView classes, there is the data layer responsible for aggregating requirements of the new data and sending the request, and further the transport layer that works with the Google API itself.

## Details view
The details view immediately reuses the available data from the list item (title, author and now enlarged image thumb) and fetches more data like description and full size cover image in the background. 

## Build

This is a standard gradle project. Use gradlew assembleDebug or gradlew assembleRelease at the project root (./gradlew if under Linux or Mac). 

## Quick preview

The pre-build app is installable from Google Play Store from.

## Authorship
This app has been initially implemented as the personal project of Audrius Meskauskas, Unterdorfwaeg 30, 8117 Switzlerland, stricly excluding any usage of any work time or equipment of his current employer. It is expected to be a community project where everyone could commit a pull request. The license is GPL 3.0. Linking is permitted with any proprietary or otherwise licensed third party libraries that come pre-installed in the Android device or ar required to interface with Google Books API.

The licensing conditions of Google Books API can be found at https://developers.google.com/books/terms. 


