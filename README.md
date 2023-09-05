#include<iostream>
#include<algorithm>
#include<climits>
using namespace std;
class Node{
    public:
    int data;
    Node *left;
    Node *right;
    Node(int d){
        data=d;
        left=NULL;
        right=NULL;
    }
    void display(Node* root) {
        if(root==NULL) return;
        display(root->left);
        display(root->right);
        cout<<root->data<<" ";
        }
};
    int size(Node* root) {
        if(root==NULL) return 0;
        return size(root->left)+size(root->right)+1;
    }
    int sum(Node *root){
    if(root==NULL) return 0;
    return root->data+sum(root->left)+sum(root->right);
    }
    int maxi(Node *root){
       if(root==NULL) return INT_MIN;
       return max(max(maxi(root->left),maxi(root->right)),root->data);
    }
int main(){
    Node* a=new Node(5);
    Node* b=new Node(10);
    Node* c=new Node(15);
    Node* d=new Node(20);
    Node* e=new Node(25);
    Node* f=new Node(30);
    Node* g=new Node(35);
    a->left=b;
    a->right=c;
    b->left=d;
    b->right=e;
    c->left=f;
    c->right=g;
    a->display(a);
    cout<<sum(a)<<endl;
    cout<<size(a)<<endl;
    cout<<maxi(a)<<endl;
    return 0;
}
