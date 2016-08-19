# dygraphite
dygraph + graphite integration to build nice Graphs with Graphite backend as a data

## Example Usage : 
#### Basic Usage
      $("#graph_load").dygraphite({
        target: [
          ['server.system.load.avg01', 'Load 1 min'],
          ['server.system.load.avg05','Load 5 min'],
          ['server.system.load.avg15','Load 15 min'],
        ],
        from:"-24hours",
      },{
        ylabel : "%"
      });

#### Synchronize Graphs :
Make sure to have your synchronize.js included :

    $(function(){
      var gs = []
      $("#graph_load").dygraphite({
        target: [
          ['server.system.load.avg01', 'Load 1 min'],
          ['server.system.load.avg05','Load 5 min'],
          ['server.system.load.avg15','Load 15 min'],
        ],
        from:"-24hours",
      },{
        ylabel : "%",
        sync: gs
      });

      $("#graph_cpu").dygraphite({
        target: [
          ['server.system.cpu.user', 'User'],
          ['server.system.cpu.system','System'],
          ['server.system.cpu.wait','I/O Wait'],
        ],
        from:"-24hours"
      },{
        ylabel : "%",
        sync: gs
      });
    })
### Options
| Option        | Default     | type    |  Details                                 | 
| ------------- |:-----------:| -------:|  ---------------------------------------:|
| from          | -24hours    | string  | graphite from string                     |
| until         | now         | string  | graphite until string                    | 
| url           | /render/    | string  | graphite api url                         |
| autoupdate    | 0           | integer | 0 = disabled else update every n seconds |
### Examples : 
##### Load Usage
![alt text](https://s3.postimg.org/gd18n6yg3/Load.png "Load Usage")
##### Memory Usage
![alt text](https://s3.postimg.org/4p76sn9b7/memory.png "Memory usage")
