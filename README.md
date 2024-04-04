#ex 7
def parse_name(text):
"""
Get the first and last name of people in the contact list 
Args: 
  text(string): represents a single line of the file
Returns:
  tuple: first and last names """
  
    first = str(re.findall('first_name = [a-z]+', text, re.IGNORECASE))

    first = first.replace('first_name = ', '')

    last = str(re.findall('last_name = [a-z]+', text, re.IGNORECASE))

    last = last.replace('last_name = ', '')

    first_and_last = (str(first), str(last))

    return first_and_last

def parse_address(text):
""" Gets address of people in contact list
    Args:
      text(string): represents a single line of the file
    Returns:
      an address object that uses the city, street, and state passed in"""

    address = str(re.findall('address = [0-9]+\s[a-z]+', text, re.IGNORECASE))

    address = str(address.replace('address = ', ''))

    address = address.split()

    state = str(re.findall(',\s[a-z]+', text, re.IGNORECASE))

    state = state.replace(', ', '')

    add = address(address[0][2:], address[1][:-2], state)

    return add

def parse_email(text):

"""Gets the email of everyone in contact list
   Args:
    text(string): Represents a single line of the file
   Returns:
     string: returns the email that is found"""
    

    email = str(re.findall('email = \w+.\w+.\w+', text, re.IGNORECASE))

    email = email.replace('email = ', '')

    return email

class address:

    def __init__(self, street, city, state):
    """Creates an object for the address
    Args:
     self: a reference to the object in question
     street(string): The street given in the address
     city(string): the city given in the address
     state(string): the state given in the address

    Returns:
     """

        self.street = street

        self.city = city

        self.state = state

class employee:

    def __init__(self, text,first_name, last_name, address, email)):
    """Creates an object for each person in the contact list
      Args:
       self: a reference to the object in question
       text(string): represents a single line of the text file
       first_name(string): first name of the person in question
       last_name(string): last name of person in question
       address(string): address of person in question
       email(string): email of person in question

        name = parse_name(text)

        self.first_name = name[0]

        self.last_name = name[1]

        self.address = parse_address(line)

        self.email = parse_email(line)
