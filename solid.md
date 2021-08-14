# SOLID

solid is a mnemonic abbreviation for a set of design principles created for software development in object oriented languages . 
the principles in solid are intended to foster simpler more robust and updatable code for software developers .

the five valid types of SOLID are:

1. Single Responsibility Principle
2. Open Closed Principle
3. Liskov Substitution Principle
4. Interface segregation Principle
5. Dependecy Inversion Principle

## Solid Responsibility Principle :
 
 The single Responsibility principle requires that a class should have only one job . so if a class has more than one responsibility it becomes coupled . A change to one responsibility results to modification of the other responsibility . 

 Let us consider a example :
```
class User:
    def __init__(self,name: str):
        self.name = name

    def get_name(self) -> str:
        pass
    
    def save(self, user:user):
        pass
```
Above is the class which has two responsibilities and it acts user properties will have to be touched and recompiled to compensate for the new changes .if we touch one it effects all other line .Let us define them into two diff classes

```
class User:
    def __init__(self, name: str):
            self.name = name
    def get_name(self):
        pass
class UserDB:
    def get_user(self, id) -> User;
        pass
    def save(self, user:User):
        pass
```
## Open-Closed Principle

In open closed principle should be open for extensions not modification . 
Let us consider a example that i have a store and ready to give a discount 

```
class Discount:
    def __init__(self,customer,price):
        self.customer = customer
        self.price = price
    def give__discount(self):
        if self.customer == 'fav':
            return self.price * 0.2
        if self.customer == 'vip':
            return self.price *0.4
```
for a new business open closed will not work for it so 
```
class Discount:
    def __init__(self, customer, price):
      self.customer = customer
      self.price = price
    def get_discount(self):
      return self.price * 0.2
class VIPDiscount(Discount):
    def get_discount(self):
      return super().get_discount() * 2

```
where vip customers will get a high discount in this.

## 3. Liskov Substitution Principle

The main idea behind Liskov Subtitution Principle is that , for any class, a client should be able to use any of its subtypes indistinguishably ,  without even noticing, and therefore without compromising the expected behavior at runtime .

```
class User():
  def __init__(self, color, board):
    create_pieces()
    self.color = color
    self.board = board
  def move(self, piece:Piece, position:int):
      piece.move(position)
      chessmate_check()
  board = ChessBoard()
  user_white = User("white", board)
  user_black = User("black", board)
  pieces = user_white.pieces
  horse = helper.getHorse(user_white, 1)
  user.move(horse)
```
Remarks on the LSP The LSP is fundamental to a good object-oriented software design because it emphasizes one of its core traits — polymorphism . It is about creating correct hierarchies so that classes derived from a base one are polymorphic along the parent one, with respect to the methods on their interface .

## Interface Segregation Principle

To illustrate this completely, we will go with a classic example because it is highly significant and easily understandable. The Classic Example

```
class IShape:
    def draw(self):
        raise NotImplementedError

class Circle(IShape):
    def draw(self):
        pass

class Square(IShape):
    def draw(self):
        pass

class Rectangle(IShape):
    def draw(self):
        pass
```
Another nice trick is that in our business logic, a single class can implement several interfaces if needed .

## Dependecy Inversion Principle

```
class AuthenticationForUser():
  def __init__(self, connector:Connector):
		self.connection = connector.connect()
	
	def authenticate(self, credentials):
		pass
	def is_authenticated(self):
		pass	
	def last_login(self):
		pass

class AnonymousAuth(AuthenticationForUser):
	pass

class GithubAuth(AuthenticationForUser):
	def last_login(self):
		pass

class FacebookAuth(AuthenticationForUser):
	pass

class Permissions()
	def __init__(self, auth: AuthenticationForUser)
		self.auth = auth
		
	def has_permissions():
		pass
		
class IsLoggedInPermissions (Permissions):
	def last_login():
		return auth.last_log
```

Solid is the key software programe to follow the best and accessible code .