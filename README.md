# Social Media Post Management System

This project implements a basic backend for managing social media posts using C++. The functionality includes adding new posts, finding posts by a specific poster, and deleting posts. The data structure used to manage the posts is a stack, which ensures that posts are handled in a last-in, first-out (LIFO) order.

## Requirements
- C++ compiler or an online C++ compiler

## Features

- **Adding a Post**: 
  After clicking 1, it will deliver you to the stack code where you can enter the image name, size, poster name, timestamp, and location. The post is then saved to the stack.

- **Finding a Post**: 
  This code searches with the poster's name because one user can post more than one image. It finds the most recent images. It also asks if you want to delete the found post or continue with the action to add a new post.

- **Deleting a Post**: 
  This function deletes the most recent posted image. It uses the stack's LIFO nature to remove the top element.

- **Saving Posts to a File**: 
  Upon ending the program, it saves all post information to a text file.
-##Canva Presentation https://www.canva.com/design/DAGFeDW1VtM/enL84GPBJ-KY9eUjDNkIfw/view?utm_content=DAGFeDW1VtM&utm_campaign=designshare&utm_medium=link&utm_source=editor##

  Choose an option:
1. Add New Post
2. Find Post
3. Delete Post
4. Save and Exit
1
Enter Image Name: beach.jpg
Enter Image Size: 1024
Poster Name: JohnDoe
Enter Image Location: California
Post saved successfully

Choose an option:
1. Add New Post
2. Find Post
3. Delete Post
4. Save and Exit
2
Enter Poster Name: JohnDoe
Image: beach.jpg
Size: 1024
Posted by: JohnDoe
Timestamp: Wed May 17 12:34:56 2023
Location: California

Do you want to delete this post? (y/n): n

Choose an option:
1. Add New Post
2. Find Post
3. Delete Post
4. Save and Exit
4
Exiting...


## How to Use

### Adding a Post
```cpp
void addPost(stack<Post>& posts) {
    Post newImage;
    cout << "Enter Image Name: ";
    cin >> newImage.name;
    cout << "Enter Image Size: ";
    cin >> newImage.size;
    cout << "Poster Name: ";
    cin >> newImage.poster;
    newImage.timestamp = time(0);
    cout << "Enter Image Location: ";
    cin >> newImage.location;
    posts.push(newImage);
    cout << "Post saved successfully" << endl;
}


### Searching Post

 bool found = false;
    stack<Post> tempStack;
    vector<Post> foundPosts;  
    while (!posts.empty()) {
        Post currPost = posts.top();
        posts.pop();
        if (currPost.poster == posterName) {
            foundPosts.push_back(currPost);
            found = true;
        }
        tempStack.push(currPost);
    }

    while (!tempStack.empty()) {
        posts.push(tempStack.top());
        tempStack.pop();
    }

    if (!found) {
        cout << "No posts found for user " << posterName << endl;
        return;
    }

### Deleting POst
```cpp
void deletePost(stack<Post>& posts) {
    if (posts.empty()) {
        cout << "No posts to delete!" << endl;
    } else {
        posts.pop();
        cout << "Most recent post deleted!" << endl;

###ending actions and saving txt file
void savePostsToFile(const stack<Post>& posts) {
    ofstream outFile("posts.txt");
    stack<Post> tempStack = posts;

    while (!tempStack.empty()) {
        Post currPost = tempStack.top();
        tempStack.pop();
        outFile << "Image: " << currPost.name << endl;
        outFile << "Size: " << currPost.size << endl;
        outFile << "Posted by: " << currPost.poster << endl;
        outFile << "Timestamp: " << asctime(localtime(&currPost.timestamp));
        outFile << "Location: " << currPost.location << endl;
        outFile << endl;
    }

    outFile.close();
    cout << "Posts saved to posts.txt" << endl;
