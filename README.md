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
<h1>Development Process</h1>
<details>

  <summary>Dialogues & Dialogue Editor</summary>
 
 
 > <details> 
 >  <summary>Dialogues</summary>
 >  <br>
 >  <div align="center">
 >   
 >  <img src="" width="60%" height="auto">
 >  </div>
 > </details>
  


</details>

 <details> 
 <summary>Leaderboard Code snippets</summary>
 <br>
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
 <br>
 > <details> 
 >  <summary> User class with only relevant methods for the Leaderboard activity, namely the comparison of users by XP</summary>
 >
 > ```java
 >public class User implements Comparable{
 >    public String id;
 >    public String nickName;
 >    public Long xp;
 >    public List<String> friends;
 >    public String description;
 >
 >    public String getXP() {
 >        return this.xp.toString();
 >    }
 >
 >    //Compares the XP of the Users
 >    @Override
 >    public int compareTo(Object o) {
 >        int compareXp = Integer.parseInt(((User)o).getXP());
 >        return compareXp-Integer.parseInt(this.xp.toString());
 >    }
 >}
 > ```
 > </details>
 <br>
 > <details> 
 >  <summary>  Leaderboard Adapter that is used to dynamically display content</summary>
 >
 > ```java
 >public class LeaderboardAdapter extends RecyclerView.Adapter<LeaderboardAdapter.RecyclerItemViewHolder> {
 >    private ArrayList<User> myList;
 >    int mLastPosition = 0;
 >
 >        public LeaderboardAdapter(ArrayList<User> myList) {
 >            this.myList = myList;
 >        }
 >
 >        public RecyclerItemViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
 >            View view = LayoutInflater.from(parent.getContext()).inflate(R.layout.user_row, parent, false);
 >            RecyclerItemViewHolder holder = new RecyclerItemViewHolder(view);
 >            return holder;
 >        }
 >        @Override
 >        public void onBindViewHolder(RecyclerItemViewHolder holder, final int position) {
 >            Log.d("onBindViewHoler ", myList.size() + "");
 >            holder.etPlaceTextView.setText(Integer.toString(position+1));
 >            holder.etNameTextView.setText(myList.get(position).getName().toString());
 >            holder.etXPTextView.setText(myList.get(position).getXP().toString());
 >           holder.crossImage.setImageResource(R.drawable.profile_pic1);
 >            mLastPosition =position;
 >        }
 >        @Override
 >        public int getItemCount() {
 >            return(null != myList?myList.size():0);
 >        }
 >        public void notifyData(ArrayList<User> myList) {
 >            Log.d("notifyData ", myList.size() + "");
 >            this.myList = myList;
 >            notifyDataSetChanged();
 >        }
 >        public class RecyclerItemViewHolder extends RecyclerView.ViewHolder {
 >            private final TextView etPlaceTextView;
 >            private final TextView etNameTextView;
 >            private final TextView etXPTextView;
 >            private CardView mainLayout;
 >            public ImageView crossImage;
 >            public RecyclerItemViewHolder(final View parent) {
 >                super(parent);
 >                etPlaceTextView = (TextView) parent.findViewById(R.id.place_textView);
 >                etNameTextView = (TextView) parent.findViewById(R.id.name_textView2);
 >                etXPTextView = (TextView) parent.findViewById(R.id.xp_textView2);
 >                crossImage = (ImageView) parent.findViewById(R.id.user_pic_imageView);
 >                mainLayout = (CardView) parent.findViewById(R.id.user_CardView);
 >            }
 >        }
 >    }
 > ```
 > <br>
 > XML file for the leaderboard layout
 > 
 > ```xml
 ><?xml version="1.0" encoding="utf-8"?>
 ><androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
 >    xmlns:app="http://schemas.android.com/apk/res-auto"
 >    xmlns:tools="http://schemas.android.com/tools"
 >    android:layout_width="match_parent"
 >    android:layout_height="match_parent"
 >    android:padding="10dp"
 >    tools:context=".LeaderboardActivity">
 >
 >    <TextView
 >        android:id="@+id/leaderboard_text"
 >        android:layout_width="match_parent"
 >        android:layout_height="wrap_content"
 >        android:layout_marginTop="25dp"
 >        android:layout_marginBottom="25dp"
 >        android:fontFamily="sans-serif-black"
 >        android:text="Leaderboard"
 >        android:textAlignment="center"
 >        android:textAllCaps="false"
 >        android:textSize="40dp"
 >        app:layout_constraintBottom_toTopOf="@+id/guideline34"
 >        app:layout_constraintEnd_toEndOf="parent"
 >        app:layout_constraintHorizontal_bias="0.0"
 >        app:layout_constraintStart_toStartOf="parent"
 >        app:layout_constraintTop_toTopOf="parent"></TextView>
 >
 >    <androidx.constraintlayout.widget.Guideline
 >        android:id="@+id/guideline34"
 >        android:layout_width="wrap_content"
 >        android:layout_height="wrap_content"
 >        android:orientation="horizontal"
 >        app:layout_constraintGuide_begin="146dp" />
 >
 >    <androidx.recyclerview.widget.RecyclerView
 >        android:id="@+id/leaderboard_recyclerview"
 >        android:layout_width="0dp"
 >        android:layout_height="0dp"
 >        android:layout_marginTop="10dp"
 >        android:layout_marginBottom="25dp"
 >        app:layout_constraintBottom_toBottomOf="parent"
 >        app:layout_constraintEnd_toEndOf="parent"
 >        app:layout_constraintStart_toStartOf="parent"
 >        app:layout_constraintTop_toTopOf="@+id/guideline34" />
 >
 ></androidx.constraintlayout.widget.ConstraintLayout>
 > ```
 > <br>
 > XML file for each user row in the leaderboard
 > 
 > ```xml
 ><?xml version="1.0" encoding="utf-8"?>
 ><androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
 >    xmlns:app="http://schemas.android.com/apk/res-auto"
 >    xmlns:tools="http://schemas.android.com/tools"
 >    android:layout_width="match_parent"
 >    android:layout_height="wrap_content"
 >    android:orientation="vertical">
 > 
 >    <com.google.android.material.card.MaterialCardView
 >       android:id="@+id/user_CardView"
 >       android:layout_width="match_parent"
 >       android:layout_height="wrap_content"
 >       android:elevation="10dp"
 >       android:layout_marginBottom="10dp"
 >       app:layout_constraintBottom_toBottomOf="parent"
 >       app:layout_constraintEnd_toEndOf="parent"
 >       app:layout_constraintStart_toStartOf="parent"
 >       app:layout_constraintTop_toTopOf="parent">
 >
 >       <androidx.constraintlayout.widget.ConstraintLayout
 >           android:layout_width="match_parent"
 >           android:layout_height="match_parent"
 >           android:orientation="vertical">
 >
 >            <ImageView
 >               android:id="@+id/user_pic_imageView"
 >               android:layout_width="80dp"
 >               android:layout_height="80dp"
 >               android:layout_marginStart="5dp"
 >               android:layout_marginTop="5dp"
 >               android:layout_marginEnd="5dp"
 >               android:layout_marginBottom="5dp"
 >               app:layout_constraintBottom_toBottomOf="parent"
 >               app:layout_constraintEnd_toStartOf="@+id/guideline13"
 >               app:layout_constraintStart_toStartOf="@+id/guideline33"
 >               app:layout_constraintTop_toTopOf="parent"
 >               app:layout_constraintVertical_bias="0.0"
 >               tools:srcCompat="@drawable/avatar" />

            <TextView
                android:id="@+id/name_textView2"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="10dp"
                android:layout_marginTop="5dp"
                android:layout_marginBottom="5dp"
                android:text="Name: "
                app:layout_constraintBottom_toTopOf="@+id/guideline12"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintHorizontal_bias="0.0"
                app:layout_constraintStart_toStartOf="@+id/guideline13"
                app:layout_constraintTop_toTopOf="parent" />

            <androidx.constraintlayout.widget.Guideline
                android:id="@+id/guideline12"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:orientation="horizontal"
                app:layout_constraintGuide_begin="41dp" />

            <androidx.constraintlayout.widget.Guideline
                android:id="@+id/guideline13"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:orientation="vertical"
                app:layout_constraintGuide_begin="161dp" />

            <TextView
                android:id="@+id/xp_textView2"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="10dp"
                android:layout_marginTop="5dp"
                android:layout_marginBottom="5dp"
                android:text="XP:"
                app:layout_constraintBottom_toBottomOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintHorizontal_bias="0.0"
                app:layout_constraintStart_toStartOf="@+id/guideline13"
                app:layout_constraintTop_toTopOf="@+id/guideline12" />

            <androidx.constraintlayout.widget.Guideline
                android:id="@+id/guideline33"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:orientation="vertical"
                app:layout_constraintGuide_begin="68dp" />

            <TextView
                android:id="@+id/place_textView"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="5dp"
                android:layout_marginTop="5dp"
                android:layout_marginEnd="5dp"
                android:layout_marginBottom="5dp"
                android:text="2"
                android:textSize="30dp"
                app:layout_constraintBottom_toBottomOf="parent"
                app:layout_constraintEnd_toStartOf="@+id/guideline33"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />


        </androidx.constraintlayout.widget.ConstraintLayout>

    </com.google.android.material.card.MaterialCardView>

</androidx.constraintlayout.widget.ConstraintLayout>
 > ```
</details>
 <details>
  <summary>Thesis</summary>
 <br>
  
  > <div align="center"> 
  >  If you are interested in obtaining more information, you can download the final presentation and the bachelor's thesis using the links provided below. These resources contain valuable insights and details about the project.
  > <br>
  > <br>
  >
  > [Presentation.pdf](https://github.com/MarsonerLaura/KingdomOfMath/files/11094274/BA.Prasentation.pptx.pdf)
  > <br>
  >
  > [Thesis.pdf](https://github.com/MarsonerLaura/KingdomOfMath/files/11094238/Thesis.pdf)
  > <br>
  > <br>
  > Abstract
  > <br>
  > Serious games have shown promise as a tool to enhance the learning experience by generating higher intrinsic motivation than traditional learning methods. In this paper, a serious game called Kingdom of Math is developed that aims to teach mathematics to secondary school students using proven design principles. To this end, essential terms and concepts are described, and related work is analyzed. The requirements for such a serious game are outlined, and the approach and design decisions made are discussed and implemented. A user study is conducted to evaluate the developed game, and the results are presented and discussed. In addition, possible improvements and enhancements for this project in the future are suggested.
  > </div>
  > <br>
> 
   
</details>
 
</p>
