# Read: Class 04 

Sequelize supports the standard associations: **One-To-One**, **One-To-Many** and **Many-To-Many**.


## One-To-One

The goal is to  setup a One-To-One relationship between models . 

* The main setup to achieve the goal is as follows:

```
model1.hasOne(model2);
model2.belongsTo(model1);
```


## Many-To-Many

Many-To-Many associations connect one source with multiple targets, while all these targets can in turn be connected to other sources beyond the first.

* The main way to do this in Sequelize is as follows:
```
const Movie = sequelize.define('Movie', { name: DataTypes.STRING });
const Actor = sequelize.define('Actor', { name: DataTypes.STRING });
Movie.belongsToMany(Actor, { through: 'ActorMovies' });
Actor.belongsToMany(Movie, { through: 'ActorMovies' });
```


## One-To-Many

One-To-Many associations are connecting one source with multiple targets, while all these targets are connected only with this single source. 

* The main way to do this is as follows:

```
Team.hasMany(Player);
Player.belongsTo(Team);

```
In summary:

* To create a One-To-One relationship, the hasOne and belongsTo associations are used together;
* To create a One-To-Many relationship, the hasMany and belongsTo associations are used together;
* To create a Many-To-Many relationship, two belongsToMany calls are used together.
* Note: there is also a Super Many-To-Many relationship, which uses six associations at once, and will be discussed in the Advanced Many-to-Many relationships guide.
This will all be seen in detail next. The advantages of using these pairs instead of one single association will be discussed in the end of this chapter.