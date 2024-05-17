Social Media Post Management System
This project implements a basic backend for managing social media posts using C++. The functionality includes adding new posts, finding posts by a specific poster, and deleting posts. The data structure used to manage the posts is a stack, which ensures that posts are handled in a last-in, first-out (LIFO) order.

REQIEREMENTS:
C++ generator||C++ online complier


#This code do mainly function of writing dates for posting projects like(Photos, videos).
#Mainly here writen the function of saving dates as like size of photo, destination where it was posted, who has loaded this post, and current time of posting.
#Finctions #1- Here code is mstly writen by stack and void function Here firstly it will ask my actions Posting, deleting post, finding post and ending actions. 
Functions #2- Addiing post. After clicking 1 it will deliver me to the stack code. There it starts like this 

  #Function #3 After this goes function of finding post. I made this code searching with poster name because it can be like there one one can post more than one image and it would be easier if we wil search with name of poster and find most recent images.

Here i also add to ask one more function for this searching code. It will ask what to do with this code delet or continue the action to add post.
#Function #4 Deleting post code will delet most recent posted image. I have to way of deleting post 1st is deleting most recent image. 
#Function #5 Ending of all code also here i add one more function saving the information in txt file after ending.

Canva Presentation https://www.canva.com/design/DAGFeDW1VtM/enL84GPBJ-KY9eUjDNkIfw/view?utm_content=DAGFeDW1VtM&utm_campaign=designshare&utm_medium=link&utm_source=editor

How to Use
Open C++ online complier
-Adding a Post-
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
Captures post details from the user and adds the new post to the stack.
-Finding a Post-
void findPost(stack<Post>& posts, const string& posterName) {
    bool found = false;
    stack<Post> tempStack;
    while (!posts.empty()) {
        Post currPost = posts.top();
        posts.pop();
        if (currPost.poster == posterName) {
            cout << "Image: " << currPost.name << endl;
            cout << "Size: " << currPost.size << endl;
            cout << "Posted by: " << currPost.poster << endl;
            cout << "Timestamp: " << asctime(localtime(&currPost.timestamp));
            cout << "Location: " << currPost.location << endl;
            cout << endl;
            found = true;
            char choice;
            cout << "Do you want to delete this post? (y/n): ";
            cin >> choice;
            if (choice == 'y' || choice == 'Y') {
                continue; // Skip pushing this post back to tempStack to effectively delete it
            }
        }
        tempStack.push(currPost);
    }
    while (!tempStack.empty()) {
        posts.push(tempStack.top());
        tempStack.pop();
    }
    if (!found) {
        cout << "No posts found for user " << posterName << endl;
    }
}
Searches for posts by the specified poster and displays them. It also asks the user if they want to delete the found post.
-Deleting a Post-
void deletePost(stack<Post>& posts) {
    if (!posts.empty()) {
        posts.pop();
        cout << "Most recent post deleted!" << endl;
    } else {
        cout << "No posts to delete!" << endl;
    }
}
Deletes the most recent post from the stack.
-Saving Posts to a File-
void savePostsToFile(const stack<Post>& posts) {
    ofstream outFile("posts.txt");
    stack<Post> tempStack = posts;
    while (!tempStack.empty()) {
        Post currPost = tempStack.top();
        outFile << currPost.name << " " << currPost.size << " " << currPost.poster << " " << asctime(localtime(&currPost.timestamp)) << " " << currPost.location << endl;
        tempStack.pop();
    }
    outFile.close();
}
Saves all posts to a text file (posts.txt) upon exiting the program.
