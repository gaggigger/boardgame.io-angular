# Boardgame.io Angular Client

 <img src="https://badge.fury.io/js/boardgame.io-angular.svg" alt="npm version" /></a>

 Angular client for [Boardgame.io](http://boardgame.io). <a href="https://www.npmjs.com/package/boardgame.io">

### Installation

```
$ npm install --save boardgame.io-angular google/boardgame.io ng-dynamic-component react react-dom uuid
```

(react dependency is needed to displaying the Debug UI from the source repository)

### usage

1) Define your [Game](http://boardgame.io/#/api/Game)
2) Define your board - all props described in [Board](http://boardgame.io/#/api/Client?id=client) are available:
   ```ts
    @Component({
      template: 'do something like {{G | json}}',
    })
    export class MyBoardComponent {
      @Input() G: any;
    }
   ```
3) import the module:
   ```ts
   import { NgModule } from '@angular/core';
   import { BoardgameIoModule } from 'boardgame.io-angular';
   
   @NgModule({
     declarations: [
       MyBoardComponent
     ],
     imports: [
       // ...
       BoardgameIoModule, // import for using bio-client
     ],
     entryComponents: [
       MyBoardComponent, // <-- must declare board as entryComponent!
     ]
   })
   export class MyModule {}
   ```
4) Add you Client view to component using `bio-client`. Properties of both board and client from are available ([Client](http://boardgame.io/#/api/Client)):
   ```
   import { MyGame } from '.';
   import { MyBoardComponent } from '.';
  
   @Component({
     template: `
       <bio-client [game]="game"
                   [numPlayers]="1"
                   [board]="board"></bio-client>
     `
   })
   export class MyExampleComponent {
     game = MyGame;               // <-- notice that we need to expose the object to the template
     board = MyBoardComponent;  
   }
   ```
5) See [more examples](https://github.com/turn-based/boardgame.io-angular/tree/master/src/app/examples)

### Running examples in this repository


```
$ git clone https://github.com/turn-based/boardgame.io-angular.git
$ cd boardgame.io-angular
$ npm i
$ npm run build 
$ npm run start
```

For Running the multiplayer examples you'll also need boardgame.io's server up and running on port 8000. An easy way to start it is running their examples script in parallel to ours:

```
$ git clone https://github.com/google/boardgame.io.git
$ cd boardgame.io
$ npm i
$ npm run examples 
```

boardgame.io's examples will run on `localhost:8000' while boardgame.io-angular examples will run on port 4200 and reuse the same server. 