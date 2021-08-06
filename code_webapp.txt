import streamlit as st
lalb = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
salb = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
spl_let = ['!','@','#','$','%','^','&','*','(',')','_','+','{','}','|']
def encrypter(endata,enkey):
    message = []
    final=[]
    for k in endata:  #HELLO
        message.append(k)        #storing the entered data as by user as LIST
    for l in message:
        try:
            if l in salb:
                a = salb.index(l)
                b = (a+enkey)%26
                c = salb[b]
                final.append(c)
            elif l in lalb:
                a = lalb.index(l)
                b = (a+enkey)%26
                c = lalb[b]
                final.append(c)
            else:
                a = spl_let.index(l)
                b = (a+enkey)%26
                c = lalb[b]
                final.append(c)
        except ValueError:
            final.append(l)
    return final


def decrypter(dedata,dekey):
    message = []
    final=[]
    for k in dedata:
        message.append(k)        #storing the entered data as by user as LIST
    for l in message:
        try:
            if l in salb:
                a = salb.index(l)
                b = (a-dekey)%26
                c = salb[b]
                final.append(c)
            elif l in lalb:
                a = lalb.index(l)
                b = (a-dekey)%26
                c = lalb[b]
                final.append(c)
            else:
                a = spl_let.index(l)
                b = (a+enkey)%26
                c = lalb[b]
                final.append(c)
        except ValueError:
            final.append(l)
    return final



#st.title('Welcome to useful app websites')
html_temp = """
	<div style="background-color:tomato;padding:3px">
	<h2 style="color:white;text-align:center;"> Gates Dashboard </h2>
	</div>
	"""
st.markdown(html_temp,unsafe_allow_html=True)


ceaser_code = st.checkbox("Ceaser Code")

c = int(input("Select a Choice from below to process your data\n1. Encrypter\n2. Decrypter\n"))
if c == 1:
    userdata1= input("Enter the text you want to Encrypt: ")
    key1 = int(input("Enter the key code to encrypt the above text: "))
    coded = encrypter(userdata1,key1)
    print ("".join(coded))
elif c == 2:
    userdata2= input("Enter the text you want to Decrypt: ")
    key2 = int(input("Enter the key code to decrypt the above text: "))
    coded = decrypter(userdata2,key2)
    print ("".join(coded))
else:
    print ("Enter a valid Choice")
