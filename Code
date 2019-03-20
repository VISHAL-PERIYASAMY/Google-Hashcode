'''Code done by VISHAL PERIYASAMY R'''

'''To open and read the contents of file'''
fileopen=open ('C:/Users/logesh/Desktop/hash/a.txt','r') 
filecontent=fileopen.readlines()
size=int(filecontent[0])

'''For storing hozitional or vertical''' 
hor_ver=[]

'''Tags are stored as value and the id's are stored as the key in the dict'''
Main_dictionary={}

'''Element and its count are stored in dict to find the root element'''
element_count_dictionary={}

'''count variable for the element id'''
element_id_count=-1

''' Final hozitional or vertical data are stored '''
final_hori_ver=[]

'''Loop to read the file data and store that in a dict '''
for i in filecontent[1::]:
    element_id_count+=1 
    list_ele=list(map(str,i.split()))
    hor_ver.append(list_ele[0])
    dummy_dictionary={}

    '''The loop to find the count of individual tags'''
    for j in list_ele[2::]:
        dummy_dictionary[j]=0
        for k in dummy_dictionary:
            if k in element_count_dictionary:
                element_count_dictionary[k]+=1
            else:
                element_count_dictionary[k]=1
                
    ''' Storing the data in a dict with id as key and tags as values'''
    Main_dictionary[element_id_count]=dummy_dictionary

    
maximum=0
root_id=0
final_id=[]

'''Loop to find the root node '''
'''The root node is determined with the assumption that the tag which has least repeating subsets are considered as root node'''
for i in Main_dictionary:
    dict_list=Main_dictionary[i]
    count_var=0
    for j in dict_list:
        if element_count_dictionary[j]==1:
            count_var+=1
    if maximum<count_var:
        maximum=count_var
        root_id=i

'''Assigning the root node'''
root=Main_dictionary[root_id]

'''Final id of the tag are appended'''
final_id.append(root_id)

'''Final Horizontal or vertical is appended''' 
final_hori_ver.append(hor_ver[root_id])

'''Deleting from the main dict'''
del Main_dictionary[root_id]

'''These three variables are used to combine V tag with another V tag'''
fla=1
flagg=1
count=0
if hor_ver[root_id]=='V':
    fla=0
    flagg=0
    count=1

'''main loop for execution'''
while len(Main_dictionary)!=0:

    '''Print to just see the program execution'''
    print(len(Main_dictionary))

    '''variable used to prevent the infinite loop'''
    prev_len=len(Main_dictionary)

    '''Loop for the main dict'''
    for index in Main_dictionary:
        flag=0

        '''Loop for the root element'''
        for i in root:
            List_root=Main_dictionary[index]
            if i in List_root:
                if fla==0 and hor_ver[index]=='V':
                    flagg=1
                if flagg:
                    final_id.append(index)
                    final_hori_ver.append(hor_ver[index])
                    root=list(List_root)
                    del Main_dictionary[index]
                    flag=1
                    break
        if hor_ver[index]=='V' and flag==1:
            fla=0
            flagg=0
            count+=1
            if count%2==0:
                count=0
                fla=1
                flagg=1
        if flag==1:
            break

    '''condition used to prevent the infinite loop'''
    if prev_len==len(Main_dictionary):
        '''Removing the content if single V is appended at the last'''
        if fla==0:
            final_id.pop()
            final_hori_ver.pop()
        break

'''Loop to map the contents as H and VV '''    
index=0
file_content=[]
while(index<len(final_id)):
    if final_hori_ver[index]=='V':
        file_content.append(sorted(final_id[index:index+2]))
        index+=2
    else:
        list_data=[]
        list_data.append(final_id[index])
        file_content.append(list_data)
        index+=1

'''To view the file content'''
print(file_content)

'''To store the output in a text file'''
file=open("C:/Users/logesh/Desktop/hash/output.txt","w")
file.write(str(len(file_content))+"\n")
for i in file_content:
    for j in i:
        file.write(str(j)+" ")
    file.write("\n")
file.close()
