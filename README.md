![Banner](https://user-images.githubusercontent.com/104200268/229340363-cde75b30-b776-4727-8847-1ac8496c8db4.png)
<p align="center"><i>PuzzleHunt</i> is a social game for mobile devices that allows players to collect Puzzle Pieces while running around in real life and combine them to complete puzzles. It also allows to gamble at dealers located around the map and to buy puzzlle pieces in shops and to trade them with friends. The longer and better the friendship is the better the trading boni between friends.</p>

<br>

<div align="center">
 
`AndroidStudio`
`Java`
`XML`
`Firebase`
`MongoDB`
`Play! Framework`
`OpenWeatherAPI`
`GitLab`
`Krita`

</div>

---

<p>
<img align="left" width="50%" height="auto" src="https://user-images.githubusercontent.com/104200268/229356173-6fc36fd0-479b-45f7-9951-6359514ab732.jpg">
 <br>
 <br>
<h1>About</h1>
<li><b>Role:</b>&emsp;&emsp;&emsp;&emsp;Programmer, Designer</li>
<li><b>Duration:</b>&emsp;&emsp;2 Months</li>
<li><b>Group Size:</b>&emsp;5</li>
<li><b>Genre:</b>&emsp;&emsp;&emsp;&nbsp;Mobile Social Game</li>
<li><b>Platform:</b>&emsp;&emsp;Android</li>
<li><b>Context:</b>&emsp;&emsp;&nbsp;Social Gaming Course</li>
</p>

<br>
<br>
<br>

<p>
<div>
<img align="right" width="47%" height="auto" src="https://user-images.githubusercontent.com/104200268/229356609-da4fde8a-7fe5-4a16-9e17-ee0c75489f78.jpg">
<br>
 <br>
<h1>Responsibilities</h1>
<li>UI Design</li>
<li>Implementation of basic activity functionality</li>
<li>Integration and usage of OpenWeatherAPI</li>
<li>Leaderboard implementation</li>
<li>Game Design</li>
<li>Storyboard creation</li>
<li>Icon creation</li>
<br>
</div>
</p>

<br>
 <br>
 
<p>
<div>
<img align="left" width="50%" height="auto" src="https://user-images.githubusercontent.com/104200268/229357404-977edd8f-7a90-4829-9a33-8aa3956f8cfb.jpg">
<br>
 <br>
 <br>
 <h1>Features</h1>
<li>Collect Puzzle-Pieces</li>
<li>Friendship Boni</li>
<li>Dealer & Shops</li>
<li>Leaderboard</li>
<li>Trade Puzzle-Pieces</li>
<li>Send Gifts</li>
<li>Weather dependent Puzzle-Piece spawning</li>
</div>
</p>

<br>
<br>
<br>

---


 <a href="http://www.youtube.com/watch?feature=player_embedded&v=zHgLsDbrP3M
" target="_blank"><img src="https://user-images.githubusercontent.com/104200268/227638337-fd73fd4e-50a8-41b3-9bd4-4d418f4fe416.png" 
alt="Watch Trailer on YouTube" align="right" width="60%" height="auto" border="10" /></a>
<br>
 <br>
  <br>
<div align="center"> Klick on the Image on the right or the button below to watch the Trailer on YouTube! 
<br>
<br>

 
[![Watch Trailer on YouTube](https://img.shields.io/badge/Watch%20Trailer-FF0000?logo=youtube&style=for-the-badge)](http://www.youtube.com/watch?feature=player_embedded&v=zHgLsDbrP3M) 

</div>

<br>
<br>


---

<p>
 
<h1>Feature Descriptions & Code Snippets</h1>

<details>
 <summary>Collect Puzzle-Pieces</summary>
</details>

<details>
 <summary>Weather dependent Puzzle-Piece spawning</summary>
</details>

<details>
 <summary>Friendship Boni</summary>
</details>

<details> 
 <summary>Dealer</summary>
</details>

<details>
 <summary>Shops</summary>
</details>

<details>
 <summary>Trade Puzzle-Pieces</summary>
</details>

<details>
 <summary>Trade Puzzle-Pieces</summary>
</details>
 
<details>
 <summary>Leaderboard</summary>
</details>

<details>
 <summary>Leaderboard Code Snippets</summary>
 
 > <details> 
 >  <summary>Leaderboard Activity class that collects all users and displays them sortet by XP Points</summary>
 >
 > ```java
 > public class LeaderboardActivity extends AppCompatActivity {
 >     private RecyclerView mRecyclerView;
 >     private LeaderboardAdapter mRecyclerAdapter;
 >     List<SetViewItem> items = new ArrayList<>();
 >     ArrayList<User> users = new ArrayList<User>();
 >     String name = "",xp = "";
 >     private final Gson gson = new Gson();
 >
 >     //Sets the layout and displays the users sortet by XP
 >     @Override
 >     protected void onCreate(Bundle savedInstanceState) {
 >         super.onCreate(savedInstanceState);
 >         setContentView(R.layout.activity_leaderboard);
 >         mRecyclerView = (RecyclerView) findViewById(R.id.leaderboard_recyclerview);
 >         mRecyclerAdapter = new LeaderboardAdapter(users);
 >         final LinearLayoutManager layoutManager = new LinearLayoutManager(this);
 >         layoutManager.setOrientation(LinearLayoutManager.VERTICAL);
 >         mRecyclerView.setLayoutManager(layoutManager);
 >         mRecyclerView.setAdapter(mRecyclerAdapter);
 >
 >         fetchUsers();
 >         sortUsersByXp();
 >         mRecyclerAdapter.notifyData(users);
 >     }
 >
 >     //Fetches the userdata from the database
 >     private void fetchUsers() {
 >         HTTPGetter get = new HTTPGetter();
 >         get.execute("user", "getAll");
 >         try {
 >             String getUserResult = get.get();
 >             if (!getUserResult.equals("{ }")) {
 >                 User[]userArr= gson.fromJson(getUserResult, User[].class);
 >                 for (User user : userArr){
 >                     users.add(user);
 >                 }
 >             }
 >         } catch (ExecutionException e) {
 >             e.printStackTrace();
 >         } catch (InterruptedException e) {
 >             e.printStackTrace();
 >         }
 >     }
 >
 >     //Sorts the Users by XP points
 >     private void sortUsersByXp(){
 >         Collections.sort(users);
 >     }
 > }
 > ```
 > </details> 
 
 > <details> 
 >  <summary>User class with only relevant methods for the Leaderboard activity, namely the comparison of users by XP</summary>
 >
 > ```java
 > public class User implements Comparable{
 >     public String id;
 >     public String nickName;
 >     public Long xp;
 >     public List<String> friends;
 >     public String description;
 >
 >     public String getXP() {
 >         return this.xp.toString();
 >     }
 >
 >     //Compares the XP of the Users
 >     @Override
 >     public int compareTo(Object o) {
 >         int compareXp = Integer.parseInt(((User)o).getXP());
 >         return compareXp-Integer.parseInt(this.xp.toString());
 >     }
 > }
 > ```
 > </details>

 > <details> 
 >  <summary>Leaderboard Adapter that is used to dynamically display content</summary>
 >
 > ```java
 > public class LeaderboardAdapter extends RecyclerView.Adapter<LeaderboardAdapter.RecyclerItemViewHolder> {
 >     private ArrayList<User> myList;
 >     int mLastPosition = 0;
 > 
 >     public LeaderboardAdapter(ArrayList<User> myList) {
 >         this.myList = myList;
 >     }
 >     
 >     //Gets and returns the current recycleritemviewholder
 >     public RecyclerItemViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
 >         View view = LayoutInflater.from(parent.getContext()).inflate(R.layout.user_row, parent, false);
 >         RecyclerItemViewHolder holder = new RecyclerItemViewHolder(view);
 >         return holder;
 >     }
 >
 >     //Sets the UI Elements (text, img) to the respective user data
 >     @Override
 >     public void onBindViewHolder(RecyclerItemViewHolder holder, final int position) {
 >         holder.etPlaceTextView.setText(Integer.toString(position+1));
 >         holder.etNameTextView.setText(myList.get(position).getName().toString());
 >         holder.etXPTextView.setText(myList.get(position).getXP().toString());
 >         holder.crossImage.setImageResource(R.drawable.profile_pic1);
 >         mLastPosition =position;
 >     }
 >
 >     @Override
 >     public int getItemCount() {
 >         return(null != myList?myList.size():0);
 >     }
 >
 >     //Notifies if user data list has changed
 >     public void notifyData(ArrayList<User> myList) {
 >         Log.d("notifyData ", myList.size() + "");
 >         this.myList = myList;
 >         notifyDataSetChanged();
 >     } 
 >
 >     //Gets the UI elements of the user row
 >     public class RecyclerItemViewHolder extends RecyclerView.ViewHolder {
 >         private final TextView etPlaceTextView;
 >         private final TextView etNameTextView;
 >         private final TextView etXPTextView;
 >         private CardView mainLayout;
 >         public ImageView crossImage;
 >         public RecyclerItemViewHolder(final View parent) {
 >             super(parent);
 >             etPlaceTextView = (TextView) parent.findViewById(R.id.place_textView);
 >             etNameTextView = (TextView) parent.findViewById(R.id.name_textView2);
 >             etXPTextView = (TextView) parent.findViewById(R.id.xp_textView2);
 >             crossImage = (ImageView) parent.findViewById(R.id.user_pic_imageView);
 >             mainLayout = (CardView) parent.findViewById(R.id.user_CardView);
 >         }
 >     }
 > }
 > ```
 > </details>
 
 > <details> 
 >  <summary>XML file for the leaderboard layout</summary>
 > 
 > ```xml
 > <?xml version="1.0" encoding="utf-8"?>
 > <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
 >     xmlns:app="http://schemas.android.com/apk/res-auto"
 >     xmlns:tools="http://schemas.android.com/tools"
 >     android:layout_width="match_parent"
 >     android:layout_height="match_parent"
 >     android:padding="10dp"
 >     tools:context=".LeaderboardActivity">
 > 
 >     <TextView
 >         android:id="@+id/leaderboard_text"
 >         android:layout_width="match_parent"
 >         android:layout_height="wrap_content"
 >         android:layout_marginTop="25dp"
 >         android:layout_marginBottom="25dp"
 >         android:fontFamily="sans-serif-black"
 >         android:text="Leaderboard"
 >         android:textAlignment="center"
 >         android:textAllCaps="false"
 >         android:textSize="40dp"
 >         app:layout_constraintBottom_toTopOf="@+id/guideline34"
 >         app:layout_constraintEnd_toEndOf="parent"
 >         app:layout_constraintHorizontal_bias="0.0"
 >         app:layout_constraintStart_toStartOf="parent"
 >         app:layout_constraintTop_toTopOf="parent"></TextView>
 >
 >     <androidx.constraintlayout.widget.Guideline
 >         android:id="@+id/guideline34"
 >         android:layout_width="wrap_content"
 >         android:layout_height="wrap_content"
 >         android:orientation="horizontal"
 >         app:layout_constraintGuide_begin="146dp" />
 >
 >     <androidx.recyclerview.widget.RecyclerView
 >         android:id="@+id/leaderboard_recyclerview"
 >         android:layout_width="0dp"
 >         android:layout_height="0dp"
 >         android:layout_marginTop="10dp"
 >         android:layout_marginBottom="25dp"
 >         app:layout_constraintBottom_toBottomOf="parent"
 >         app:layout_constraintEnd_toEndOf="parent"
 >         app:layout_constraintStart_toStartOf="parent"
 >         app:layout_constraintTop_toTopOf="@+id/guideline34" />
 >
 > </androidx.constraintlayout.widget.ConstraintLayout>
 > ```
 > </details>
 
 > <details> 
 >  <summary>XML file for each user row in the leaderboard</summary>
 > 
 > ```xml
 > <?xml version="1.0" encoding="utf-8"?>
 > <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
 >     xmlns:app="http://schemas.android.com/apk/res-auto"
 >     xmlns:tools="http://schemas.android.com/tools"
 >     android:layout_width="match_parent"
 >     android:layout_height="wrap_content"
 >     android:orientation="vertical">
 >  
 >     <com.google.android.material.card.MaterialCardView
 >         android:id="@+id/user_CardView"
 >         android:layout_width="match_parent"
 >         android:layout_height="wrap_content"
 >         android:elevation="10dp"
 >         android:layout_marginBottom="10dp"
 >         app:layout_constraintBottom_toBottomOf="parent"
 >         app:layout_constraintEnd_toEndOf="parent"
 >         app:layout_constraintStart_toStartOf="parent"
 >         app:layout_constraintTop_toTopOf="parent">
 >  
 >         <androidx.constraintlayout.widget.ConstraintLayout
 >             android:layout_width="match_parent"
 >             android:layout_height="match_parent"
 >             android:orientation="vertical">
 >  
 >             <ImageView
 >                 android:id="@+id/user_pic_imageView"
 >                 android:layout_width="80dp"
 >                 android:layout_height="80dp"
 >                 android:layout_marginStart="5dp"
 >                 android:layout_marginTop="5dp"
 >                 android:layout_marginEnd="5dp"
 >                 android:layout_marginBottom="5dp"
 >                 app:layout_constraintBottom_toBottomOf="parent"
 >                 app:layout_constraintEnd_toStartOf="@+id/guideline13"
 >                 app:layout_constraintStart_toStartOf="@+id/guideline33"
 >                 app:layout_constraintTop_toTopOf="parent"
 >                 app:layout_constraintVertical_bias="0.0"
 >                 tools:srcCompat="@drawable/avatar" />
 >
 >             <TextView
 >                 android:id="@+id/name_textView2"
 >                 android:layout_width="wrap_content"
 >                 android:layout_height="wrap_content"
 >                 android:layout_marginStart="10dp"
 >                 android:layout_marginTop="5dp"
 >                 android:layout_marginBottom="5dp"
 >                 android:text="Name: "
 >                 app:layout_constraintBottom_toTopOf="@+id/guideline12"
 >                 app:layout_constraintEnd_toEndOf="parent"
 >                 app:layout_constraintHorizontal_bias="0.0"
 >                 app:layout_constraintStart_toStartOf="@+id/guideline13"
 >                 app:layout_constraintTop_toTopOf="parent" />
 >
 >             <androidx.constraintlayout.widget.Guideline
 >                 android:id="@+id/guideline12"
 >                 android:layout_width="wrap_content"
 >                 android:layout_height="wrap_content"
 >                 android:orientation="horizontal"
 >                 app:layout_constraintGuide_begin="41dp" />
 > 
 >             <androidx.constraintlayout.widget.Guideline
 >                 android:id="@+id/guideline13"
 >                 android:layout_width="wrap_content"
 >                 android:layout_height="wrap_content"
 >                 android:orientation="vertical"
 >                 app:layout_constraintGuide_begin="161dp" />
 > 
 >             <TextView
 >                 android:id="@+id/xp_textView2"
 >                 android:layout_width="wrap_content"
 >                 android:layout_height="wrap_content"
 >                 android:layout_marginStart="10dp"
 >                 android:layout_marginTop="5dp"
 >                 android:layout_marginBottom="5dp"
 >                 android:text="XP:"
 >                 app:layout_constraintBottom_toBottomOf="parent"
 >                 app:layout_constraintEnd_toEndOf="parent"
 >                 app:layout_constraintHorizontal_bias="0.0"
 >                 app:layout_constraintStart_toStartOf="@+id/guideline13"
 >                 app:layout_constraintTop_toTopOf="@+id/guideline12" />
 > 
 >             <androidx.constraintlayout.widget.Guideline
 >                 android:id="@+id/guideline33"
 >                 android:layout_width="wrap_content"
 >                 android:layout_height="wrap_content"
 >                 android:orientation="vertical"
 >                 app:layout_constraintGuide_begin="68dp" />
 > 
 >             <TextView
 >                 android:id="@+id/place_textView"
 >                 android:layout_width="wrap_content"
 >                 android:layout_height="wrap_content"
 >                 android:layout_marginStart="5dp"
 >                 android:layout_marginTop="5dp"
 >                 android:layout_marginEnd="5dp"
 >                 android:layout_marginBottom="5dp"
 >                 android:text="2"
 >                 android:textSize="30dp"
 >                 app:layout_constraintBottom_toBottomOf="parent"
 >                 app:layout_constraintEnd_toStartOf="@+id/guideline33"
 >                 app:layout_constraintStart_toStartOf="parent"
 >                 app:layout_constraintTop_toTopOf="parent" />
 >
 >         </androidx.constraintlayout.widget.ConstraintLayout>
 >
 >     </com.google.android.material.card.MaterialCardView>
 >
 > </androidx.constraintlayout.widget.ConstraintLayout>
 > ```
 > </details>
</details>
 
<h1>Development Process</h1>
<details>
  <summary>Feature Brainstorming</summary>
 
 > At the beginning of the development process each of the teammembers had to sketch out and detail 3 potential features for the game. 
 
 > <details> 
 >  <summary>My Contributions</summary>
 >  <br>
 >  <div align="center">
 >  One of the first ideas was to create Eventbased Puzzles. For example at valentines day or at christmas special puzzles are possible to get but only for a short duration of 1 or 2 weeks. The image below shows the first sketch of the idea and the pages.
 >  <img src="https://user-images.githubusercontent.com/104200268/229362847-0351d3a5-9396-421b-81bf-f4edf67b0354.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  This picture shows the idea of Eventbased Puzzles after polishing it.
 >  <img src="https://user-images.githubusercontent.com/104200268/229362853-41b7f7eb-fd15-40db-954a-2fb1e0cb2c9c.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Another idea was to let the current weather influence the type of Puzzle-Pieces that are spawned. This shows the initial sketch of the different weather types.
 >  <img src="https://user-images.githubusercontent.com/104200268/229362856-9665ad66-43e2-4645-958b-6dc8d980cb98.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  This image shows the polished sketch of Weatherbased Puzzle-Piece spawning.
 >  <img src="https://user-images.githubusercontent.com/104200268/229362859-8a2d2c92-5919-42c7-9069-8bd7c64ccad8.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  This picture shows the initial sketch of Puzzle-Pieces Shops where players can buy or exchange Puzzle-Pieces.
 >  <img src="https://user-images.githubusercontent.com/104200268/229362863-7bb368e2-4b34-4a97-abf0-ceb01ada85f0.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  This image shows the polished sketch of the Puzzle-Pieces Shop.
 >  <img src="https://user-images.githubusercontent.com/104200268/229362867-7839888e-246f-43d1-aeeb-557613c48a37.png" width="90%" height="auto">
 >  </div>
 > </details>
 
 > <details> 
 >  <summary>Other Teammembers Contributions</summary>
 >  <br>
 >  <div align="center">
 >  Puzzle Preferences
 >  <img src="https://user-images.githubusercontent.com/104200268/229362883-a996cbbb-b4ef-4b21-8909-368201c7bc8c.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Collect Puzzle-Pieces outdoor
 >  <img src="https://user-images.githubusercontent.com/104200268/229362884-d9450c14-cdf3-43df-8355-b992bbe00623.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Lootboxes
 >  <br>
 >  <img src="https://user-images.githubusercontent.com/104200268/229362885-988beed1-a202-4619-9b8a-1c71e62ca085.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Trade Puzzle-Pieces
 >  <img src="https://user-images.githubusercontent.com/104200268/229362886-d2b1269d-b02a-43dc-bf07-1fe8d2f19dfd.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Create Puzzles
 >  <img src="https://user-images.githubusercontent.com/104200268/229362889-03da8651-9582-4138-9533-e29206ececf7.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Solve Puzzles
 >  <img src="https://user-images.githubusercontent.com/104200268/229362892-90eeaa2a-80f0-4f91-a6d6-69ffe2b2546c.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Friendship Level/XP
 >  <img src="https://user-images.githubusercontent.com/104200268/229362963-b7e874af-fae9-45ad-9eb6-7fb4488b9b92.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Use POI as Images for Puzzles
 >  <img src="https://user-images.githubusercontent.com/104200268/229362987-5779384d-8c8a-471d-8af5-17b71967614c.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Leaderboard & Rewards based on Ranking
 >  <img src="https://user-images.githubusercontent.com/104200268/229362879-b2533d0f-3ea5-4faf-bca7-c674e62d083e.png" width="70%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Dealer
 >  <img src="https://user-images.githubusercontent.com/104200268/229362974-21e9e99c-55a2-44f2-bcf8-45e7c718c0fd.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Schnitzeljagt
 >  <img src="https://user-images.githubusercontent.com/104200268/229362977-ed8066e0-d99c-4dfa-a551-c401def431eb.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Puzzle of the week
 >  <img src="https://user-images.githubusercontent.com/104200268/229362980-7edfbb58-8c30-4fe5-a5ea-029596a6000c.png" width="90%" height="auto">
 >  </div>
 >  <br>
 >  <div align="center">
 >  Finishing Puzzles
 >  <img src="https://user-images.githubusercontent.com/104200268/229362981-948895db-5e19-4dfb-9b38-2940a2fc567d.png" width="60%" height="auto">
 >  </div>
 > </details>
 <img src="https://user-images.githubusercontent.com/104200268/229362989-1de4292a-624f-40fb-9c28-9c283472aa26.png" width="90%" height="auto">
 
<details>

  <summary>Storyboard</summary>
 ![storyboard-01](https://user-images.githubusercontent.com/104200268/229363088-d3b05454-a447-4841-b901-398ac13980cd.png)
![storyboard-02](https://user-images.githubusercontent.com/104200268/229363089-7508d1d0-6f94-4fea-9fc6-61440713216a.png)
![storyboard-03](https://user-images.githubusercontent.com/104200268/229363091-58a53810-7e83-49d5-99b9-b7744dad8f1e.png)
![storyboard-04](https://user-images.githubusercontent.com/104200268/229363093-b0315115-11c0-4129-8c77-a2143de9b2ff.png)
![storyboard-05](https://user-images.githubusercontent.com/104200268/229363096-04713ef1-2fb8-4222-b211-53aacc1476b4.png)
![storyboard-06](https://user-images.githubusercontent.com/104200268/229363098-8860957f-b124-40fd-ab40-dd4f28c76524.png)

![storyboard-07](https://user-images.githubusercontent.com/104200268/229363057-e2e9d929-9186-412f-9f83-f72552bd0eac.png)
![storyboard-08](https://user-images.githubusercontent.com/104200268/229363059-e2786c9c-5f9c-4e3c-a975-081f5dda825e.png)
![storyboard-09](https://user-images.githubusercontent.com/104200268/229363060-de10bc87-a998-49d5-897c-95a2dd958899.png)
![storyboard-10](https://user-images.githubusercontent.com/104200268/229363061-1a2ce8e0-0cfe-47cf-826c-ec556dfb8078.png)
![storyboard-11](https://user-images.githubusercontent.com/104200268/229363064-3da5df2f-dc49-4e45-bd81-ba7563e244cf.png)
![storyboard-12](https://user-images.githubusercontent.com/104200268/229363066-951bebaf-9a87-48ee-992e-fd93880e8b40.png)
![storyboard-13](https://user-images.githubusercontent.com/104200268/229363068-683eff2c-8bd1-4d18-80f8-ade098dee1da.png)
![storyboard-14](https://user-images.githubusercontent.com/104200268/229363070-9ff4573d-f4c0-4788-ad0c-b764281622e1.png)
![storyboard-15](https://user-images.githubusercontent.com/104200268/229363071-ce24073d-07c2-4e2e-b876-f5f92c58569c.png)
![storyboard-16](https://user-images.githubusercontent.com/104200268/229363072-a1bfbb7c-db89-48ac-a5a0-d7a353d61d1c.png)
![storyboard-17](https://user-images.githubusercontent.com/104200268/229363074-01cb53a0-b0b8-48bf-8d98-31b19eca372b.png)
![storyboard-18](https://user-images.githubusercontent.com/104200268/229363075-d9defff0-d184-485b-a3c8-8ada57c74a97.png)
![storyboard-19](https://user-images.githubusercontent.com/104200268/229363077-f0f51e71-ecbf-4ccb-b621-cb715a52d6d0.png)
![storyboard-20](https://user-images.githubusercontent.com/104200268/229363079-a79b59b5-17e7-4ad2-b849-baf4e45b9bb6.png)
![storyboard-21](https://user-images.githubusercontent.com/104200268/229363081-7e3b9afe-b2ca-41e2-a1e5-d0c5f30280ff.png)
![storyboard-22](https://user-images.githubusercontent.com/104200268/229363082-3878b765-2a4d-40f4-94c0-5a21a840743a.png)
![storyboard-23](https://user-images.githubusercontent.com/104200268/229363083-7716c688-ccf1-43c6-8742-703b8a35eeaf.png)
![storyboard-24](https://user-images.githubusercontent.com/104200268/229363086-6b84fd5e-58ec-4ad6-9cd2-003a3e4818a6.png)
![storyboard-25](https://user-images.githubusercontent.com/104200268/229363087-002b64ee-4805-4602-8a96-c6546321f55e.png)


</details>
 
<details>
 <summary>Pages</summary>
 <br>

 >  <div align="center">
 >  To have a better overview of the different pages, how they look like and how they are connected I created a diagram that displays everything.
 >  <br>
 >  <img src="https://user-images.githubusercontent.com/104200268/229363879-1448290e-1691-4bcb-9614-39bd7111cdf8.jpg" width="70%" height="auto">
 >  <br>
 >  As the image is pretty small and it needs to be zoomed in to see the details, it is linked as a PDF to download below:
 >
 >  [pages.pdf](https://github.com/MarsonerLaura/PuzzleHunt/files/11132658/pages.pdf)
 >  </div>
 >  <br>
 
</details> 
  
 
<details>
 <summary>Presentation</summary>
 <br>
 
 >  <div align="center">
 >  To summarize the features and technologies used the final presentation is linked below:
 >  <br>
 >
 >  [Präsentation Social Gaming.pdf](https://github.com/MarsonerLaura/PuzzleHunt/files/11132678/Prasentation.Social.Gaming.pdf)
 > </div>
 > <br>
 
</details> 


 
</p>
