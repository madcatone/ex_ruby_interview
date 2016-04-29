# ruby 面試題目

#### 題目1. What's the difference between equal?, eql?, ===, and ==?

http://stackoverflow.com/questions/7156955/whats-the-difference-between-equal-eql-and

#### 題目2. array = [22,2,66,-2,55,0] , 請使用快速排序 .

```ruby
[22,2,66,-2,55,0].sort
```

```ruby
 def quicksort(list)
  return [] if list.size == 0
  x, *xs = *list
  less, more = xs.partition{|y| y < x}
  quicksort(less) + [x] + quicksort(more)
 end
```

```ruby
 def quicksort(l)
  return [] if (x,*xs=l).empty?
  less, more = xs.partition{|y| y < x}
  quicksort(less) + [x] + quicksort(more)
 end
```

```ruby
 def quicksort a
  (pivot = a.pop) ? quicksort(a.select{|i| i <= pivot}) + [pivot] + quicksort(a.select{|i| i > pivot}) : []
 end
```

#### 題目3. 文件在 /home/root/demo.txt 下, 請寫方法讀取 demo.txt 内容 . (加分題: 讀取*指定路徑*下文件内容)

```ruby
File.read("/home/root/demo.txt")
```

```ruby
def read name
  File.read("#{name}")
end
```

#### 題目4. 字串: str = "hello word ruby" , 寫出至少兩種方式擷取出 "word" 字串.

```ruby
str[6..9]
```

```ruby
str[-9..-6]
```

#### 題目5. names = %w(hello good res start end string me submit), 找出 names 中以"s"開頭的單字, 並把該單字轉成大寫的方法.

```ruby
names.select { |name| name.start_with?('S') }.map(&:upcase)
```

#### 題目6. 求「20以内的平方可被5整除的自然數的和」 之方法？

```ruby
n, num_elements, sum = 1, 0, 0
while num_elements < 100
  if n**2 % 5 == 0
    sum += n
    num_elements += 1
  end
  n += 1
end
sum #=> 25250
```

#### 题目7. 以下Animal.new.speak , Animal.speak,  Dog.speak 和 Dog.new.speak 分别輸出结果 ? 並說明原因 .

```ruby
#animal.rb
class Animal
  def speak
    puts "Ou! Ou ....."
  end

  def self.speak
    puts "Quack! Quack... "
  end
end

#dog.rb
class Dog < Animal
  def speak
    puts 'Wang! Wang... '
  end
end
```

