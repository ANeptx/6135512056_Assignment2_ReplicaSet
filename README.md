# 6135512056_Assignment2_ReplicaSet

mkdir cm_replica_demo

cd cm_replica_demo

mkdir r1

mkdir r2

mkdir r3


 mongod --replSet 6135512056 --logpath ./r1.log --dbpath ./r1 --port 27018 & 

mongod --replSet 6135512056 --logpath ./r2.log --dbpath ./r2 --port 27019 &

mongod --replSet 6135512056 --logpath ./r3.log --dbpath ./r3 --port 27020 &


mongo --port 27018   

config = {_id: "6135512056", members:[

   {_id: 0, host: "localhost:27018"},
  
   {_id: 1, host: "localhost:27019"},
 
   {_id: 2, host: "localhost:27020"}]
 
};


rs.initiate(config);

rs.status();


mongo --host 6135512056/localhost:27018,localhost:27019,localhost:27020

use chitsanupong

db.getCollection('test').find({})
