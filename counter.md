import 'dart:ffi';
import 'dart:io';

void main(List<String> arguments) {
  
  int opValue;
  int n1;
  int n2;
  String? tempInput;
  int choice;
  bool stop=false;
  
  Counter Counter;

  print("Enter 2 numbers");

  tempInput=stdin.readLineSync();

  if(tempInput!=null && tempInput.isNotEmpty)
  {
  n1 = int.parse(tempInput);
  }
  else{
    n1=0;
  }
  
   tempInput=stdin.readLineSync();

  if(tempInput!=null && tempInput.isNotEmpty)
  {
  n2 = int.parse(tempInput);
  }
  else{
    n2=0;
  }

  print("Enter username");
  tempInput=stdin.readLineSync();
  
  if(tempInput!=null && tempInput.isNotEmpty)
  {
  Counter = Counter(userName:tempInput,
                                count:100,
                                multiply:0,
                                divide:0,
                                remainder:0,
                                );
  }
  else{
    return;
  }


 print("Enter value for increment/decrement");

   tempInput=stdin.readLineSync();

  if(tempInput!=null && tempInput.isNotEmpty)
  {
  opValue = int.parse(tempInput);
  }
  else{
    opValue=0;
  }
  
  while(!stop)
  {

  print('''Enter choice
           1. Print Value
           2. Increment
           3. Decrement
           4. Change Username
           5. Multiply
           6. Divide
           7. Remainder
           8. Stop''');

  tempInput=stdin.readLineSync();
  if(tempInput!=null && tempInput.isNotEmpty)
  {
  choice = int.parse(tempInput);
  }
  else{
    choice=0;
  }
 
print("Starting value of counter is : ${Counter.count} and username is ${Counter.userName}");
print("Starting Mulitplication value is : ${Counter.multiply}");
print("Starting Division value is : ${Counter.divide}");
print("Starting Remainder value is : ${Counter.remainder}\n\n");

  switch(choice){
    case 1: print(Counter);
            break; 
    case 2: incrementCounter(counter:Counter,incrementValue:opValue);     
            break;
    case 3: decrementCounter(counter:Counter,decrementValue:opValue);
            break;
    case 4: changeUserName(Counter:Counter);
            break;
    case 5: multiplyNumbers(multi:Counter,n1:n1,n2:n2);
    break;
    
    case 6: divideNumbers(div:Counter,n1:n1,n2:n2);
    break;

    case 7: remainderofNumbers(rem:Counter,n1:n1,n2:n2);
    break;
    case 8:
          stop=true;
          break;

    default:
    print('Wrong choice');

  }
  print("Current value of counter is : ${Counter.count} and username is ${Counter.userName}");
  print("Current Mulitplication value is : ${Counter.multiply}");
  print("Current Division value is : ${Counter.divide}");
  print("Current Remainder value is : ${Counter.remainder}\n\n");
  }
  print("Final value of counter is : ${Counter.count} and username is ${Counter.userName}");
  print("Final Mulitplication value is : ${Counter.multiply}");
  print("Final Division value is : ${Counter.divide}");
  print("Final Remainder value is :${Counter.remainder}");
}

void changeUserName({required Counter Counter}){
print("Enter new username");
String? tempInput=stdin.readLineSync();
if(tempInput!=null && tempInput.isNotEmpty)
{
  Counter.userName=tempInput;
}
}

void incrementCounter({required Counter counter, required int incrementValue})
  {
    counter.count=counter.count+incrementValue; 
  }

  void decrementCounter({required Counter counter, required int decrementValue})
  {
    counter.count=counter.count-decrementValue;    
  }

  void multiplyNumbers({required Counter multi,required int n1,required int n2})
  {
    multi.multiply = n1*n2; 
  }

  void divideNumbers({required Counter div,required int n1,required int n2})
  {
    if(n2==0){
     print("Divide by zero");
    }
    else{
      div.divide = n1/n2;
    } 
  }

  void remainderofNumbers({required Counter rem,required int n1,required int n2})
  {
    rem.remainder = n1%n2; 
  }

  class Counter{
    int count;
    String userName;
    int multiply;
    double divide;
    int remainder;

    Counter({required this.count, required this.userName,required this.multiply,required this.divide,required this.remainder});
  }
