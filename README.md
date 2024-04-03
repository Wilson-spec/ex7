#ex 7
def parse_name(text):
    first = str(re.findall('first_name = [a-z]+', text, re.IGNORECASE))

    first = first.replace('first_name = ', '')

    last = str(re.findall('last_name = [a-z]+', text, re.IGNORECASE))

    last = last.replace('last_name = ', '')

    first_and_last = (str(first), str(last))

    return first_and_last

def parse_address(text):

    address = str(re.findall('address = [0-9]+\s[a-z]+', text, re.IGNORECASE))

    address = str(address.replace('address = ', ''))

    address = address.split()

    state = str(re.findall(',\s[a-z]+', text, re.IGNORECASE))

    state = state.replace(', ', '')

    add = address(address[0][2:], address[1][:-2], state)

    return add

def parse_email(text):

    email = str(re.findall('email = \w+.\w+.\w+', text, re.IGNORECASE))

    email = email.replace('email = ', '')

    return email

class address:

    def __init__(self, street, city, state):

        self.street = street

        self.city = city

        self.state = state

class employee:

    def __init__(self, text,first_name, last_name, address, email)):

        name = parse_name(text)

        self.first_name = name[0]

        self.last_name = name[1]

        self.address = parse_address(line)

        self.email = parse_email(line)
