**`downcase`** sẽ trả về `nil` nếu như string không có thay đổi.  
Ví dụ:  
```ruby
"FiShInG".downcase! # return: fishing
"fishing".downcase! # return: nil
```

Vì vậy, cần cẩn thận **không** dùng ghép `downcase!` với các câu lệnh khác, đề phòng trường hợp kết quả không mong muốn, như trường hợp sau:  
```ruby
class Person
  attr_reader :hobbies

  def initialize
    @hobbies = []
  end

  def has_hobby hobby
    @hobbies << hobby.downcase! unless @hobbies.includes? hobby
  end
end

person = Person.new
person.has_hobby "Fishing"

# Expected: ["fishing"]
# Got: [nil]
p person.hobbies
```

Tương tự, cần cẩn trọng khi dùng các hàm xử lý string khác như `upcase!`, `swapcase!`, `capitalize!`.