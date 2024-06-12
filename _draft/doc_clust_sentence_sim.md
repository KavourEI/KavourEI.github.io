---
layout: post
current: post
cover:  assets/images/lda_fund/lda_basic_0.jpg
navigation: True
title: Document Clustering - Sentence Similarity
date: 2022-6-11
tags: [Machine Learning, NLP]
class: post-template
subclass: 'post'
author: Kavour
---

<p>This analysis is completed in R programming language. One can find the project as well as the data, to follow along Kaggle and to be more precise Document Clustering. There are some tasks preset in kaggle. I am not going to complete them all though I will complete the ones I believe have meaning, as I believe that the rest are a repetition of the ones completed here.</p>

<h2 id="specialformatting">Introduction</h2>

<p>This project is about the similarity level of 22 sentences. Those sentences are related to an animal and to be more precise they are cat related sentences. In this project, I am going to load the sentences, make some transformations, and then use the cosine distance as to find the ones that are most likely to have the same meaning according to the aforementioned algorithm. Apart from that, I am going use hierarchical clustering machine learning method, in order to create a plot of the alike sentences to the first one, and see whether we are going to have the same results. Without further do and leaving aside the hesitation, it is time to begin our analysis. Initially, I am going to load the libraries that we are going to use here.</p>

<p>Before importing our data, there is a need to define a function that we are going to use later on. I am going to explain how this function works when the time comes, so please be patient and curious! 😉</p>

<pre><code>
nr_values <- function(dist_val, number, type){
  if (number < length(dist_val)){
    if (number<1){
      stop("Not valid number!")
      } else if (number == 1){
        if (type == "least"){
          cat(which(min(dist_val, na.rm = TRUE) == dist_val), "-", min(dist_val, na.rm = TRUE))
          } else if (type == "most"){
            cat(which(max(dist_val[2:length(dist_val)], na.rm = TRUE) == dist_val), "-", max(dist_val[2:length(dist_val)], na.rm = TRUE))
            } else if (type != "least" && type != "most" ){
              stop("Not valid type!")
              }
        } else if(number >1){
          if (type == "least"){
            for (i in 1:number){
              value_ <- head(tail(sort(dist_val, decreasing = TRUE), i),1)
              cat(value_,"(",which(value_==dist_val),")", "\n")
              }
            } else if (type == "most"){
              for (i in 1:number){
                value_ <- head(tail(sort(dist_val[2:length(dist_val)], decreasing = FALSE), i),1)
                cat(value_,"(",which(value_==dist_val),")", "\n")
                }
              } else if (type != "least" && type != "most" ){
                stop("Not valid type!")
              }
        }
  } else {
      stop("Number not supported!")
    }
}
</code></pre>

<p>Now we are ready to load our data, and read for the first time the sentences. Get a hold on yourself. It may be confusing at this point to read them.</p>

<pre><code>
file_path <- c('/Users/words.txt')
file <- readtext(file = file_path)
file$text

## [1] "In comparison to dogs, cats have not undergone major changes during the domestication process.\nAs cat simply catenates streams of bytes, it can be also used to concatenate binary files, where it will just concatenate sequence of bytes.\nA common interactive use of cat for a single file is to output the content of a file to standard output.\nCats can hear sounds too faint or too high in frequency for human ears, such as those made by mice and other small animals.\nIn one, people deliberately tamed cats in a process of artificial selection, as they were useful predators of vermin.\nThe domesticated cat and its closest wild ancestor are both diploid organisms that possess 38 chromosomes and roughly 20,000 genes.\nDomestic cats are similar in size to the other members of the genus Felis, typically weighing between 4 and 5 kg (8.8 and 11.0 lb).\nHowever, if the output is piped or redirected, cat is unnecessary.\ncat with one named file is safer where human error is a concern - one wrong use of the default redirection symbol \">\" instead of \"<\" (often adjacent on keyboards) may permanently delete the file you were just needing to read.\nIn terms of legibility, a sequence of commands starting with cat and connected by pipes has a clear left-to-right flow of information.\nCat command is one of the basic commands that you learned when you started in the Unix / Linux world.\nUsing cat command, the lines received from stdin can be redirected to a new file using redirection symbols.\nWhen you type simply cat command without any arguments, it just receives the stdin content and displays it in the stdout.\nLeopard was released on October 26, 2007 as the successor of Tiger (version 10.4), and is available in two editions.\nAccording to Apple, Leopard contains over 300 changes and enhancements over its predecessor, Mac OS X Tiger.\nAs of Mid 2010, some Apple computers have firmware factory installed which will no longer allow installation of Mac OS X Leopard.\nSince Apple moved to using Intel processors in their computers, the OSx86 community has developed and now also allows Mac OS X Tiger and later releases to be installed on non-Apple x86-based computers.\nOS X Mountain Lion was released on July 25, 2012 for purchase and download through Apple's Mac App Store, as part of a switch to releasing OS X versions online and every year.\nApple has released a small patch for the three most recent versions of Safari running on OS X Yosemite, Mavericks, and Mountain Lion.\nThe Mountain Lion release marks the second time Apple has offered an incremental upgrade, rather than releasing a new cat entirely.\nMac OS X Mountain Lion installs in place, so you won't need to create a separate disk or run the installation off an external drive.\nThe fifth major update to Mac OS X, Leopard, contains such a mountain of features - more than 300 by Apple's count."
</code></pre>

<p>Let’s take a step forward and make things a bit clearer. Here we are going to split the file and convert it to list of sentences. Let’s take a look at the first three sentences of the list we just created.</p>

<pre><code>
spliting_at <- c('\n')
file_splitted <- str_split(file$text,pattern = spliting_at)
file_splitted[[1]][1:3]

## [1] "In comparison to dogs, cats have not undergone major changes during the domestication process."                                              
## [2] "As cat simply catenates streams of bytes, it can be also used to concatenate binary files, where it will just concatenate sequence of bytes."
## [3] "A common interactive use of cat for a single file is to output the content of a file to standard output."
</code></pre>


<p>I am going to “unlist” the item and keep only the sentences. So, please keep a hold on yourself, I am going to show you the sentences. Maybe while you read them, note down the ones that you think have similar meaning to the first and compare your notes to the results we are going to end up with.</p>

<pre><code>
sentences <- file_splitted[[1]]
sentences

##  [1] "In comparison to dogs, cats have not undergone major changes during the domestication process."                                                                                                                                       
##  [2] "As cat simply catenates streams of bytes, it can be also used to concatenate binary files, where it will just concatenate sequence of bytes."                                                                                         
##  [3] "A common interactive use of cat for a single file is to output the content of a file to standard output."                                                                                                                             
##  [4] "Cats can hear sounds too faint or too high in frequency for human ears, such as those made by mice and other small animals."                                                                                                          
##  [5] "In one, people deliberately tamed cats in a process of artificial selection, as they were useful predators of vermin."                                                                                                                
##  [6] "The domesticated cat and its closest wild ancestor are both diploid organisms that possess 38 chromosomes and roughly 20,000 genes."                                                                                                  
##  [7] "Domestic cats are similar in size to the other members of the genus Felis, typically weighing between 4 and 5 kg (8.8 and 11.0 lb)."                                                                                                  
##  [8] "However, if the output is piped or redirected, cat is unnecessary."                                                                                                                                                                   
##  [9] "cat with one named file is safer where human error is a concern - one wrong use of the default redirection symbol \">\" instead of \"<\" (often adjacent on keyboards) may permanently delete the file you were just needing to read."
## [10] "In terms of legibility, a sequence of commands starting with cat and connected by pipes has a clear left-to-right flow of information."                                                                                               
## [11] "Cat command is one of the basic commands that you learned when you started in the Unix / Linux world."                                                                                                                                
## [12] "Using cat command, the lines received from stdin can be redirected to a new file using redirection symbols."                                                                                                                          
## [13] "When you type simply cat command without any arguments, it just receives the stdin content and displays it in the stdout."                                                                                                            
## [14] "Leopard was released on October 26, 2007 as the successor of Tiger (version 10.4), and is available in two editions."                                                                                                                 
## [15] "According to Apple, Leopard contains over 300 changes and enhancements over its predecessor, Mac OS X Tiger."                                                                                                                         
## [16] "As of Mid 2010, some Apple computers have firmware factory installed which will no longer allow installation of Mac OS X Leopard."                                                                                                    
## [17] "Since Apple moved to using Intel processors in their computers, the OSx86 community has developed and now also allows Mac OS X Tiger and later releases to be installed on non-Apple x86-based computers."                            
## [18] "OS X Mountain Lion was released on July 25, 2012 for purchase and download through Apple's Mac App Store, as part of a switch to releasing OS X versions online and every year."                                                      
## [19] "Apple has released a small patch for the three most recent versions of Safari running on OS X Yosemite, Mavericks, and Mountain Lion."                                                                                                
## [20] "The Mountain Lion release marks the second time Apple has offered an incremental upgrade, rather than releasing a new cat entirely."                                                                                                  
## [21] "Mac OS X Mountain Lion installs in place, so you won't need to create a separate disk or run the installation off an external drive."                                                                                                 
## [22] "The fifth major update to Mac OS X, Leopard, contains such a mountain of features - more than 300 by Apple's count."
</code></pre>

<p>I hope you have found and note down some sentences as said earlier. We are going now to use a for-loop, in order to convert all the sentences to lowercase.</p>

<pre><code>
lowcase_sentences <- c()
for(i in 1:length(sentences)){
  a <- tolower(sentences[i])
  undot <- gsub('\\.','',a)
  lowcase_sentences[i] <- undot
}
lowcase_sentences[1:3]

##  [1] "in comparison to dogs, cats have not undergone major changes during the domestication process"                                                                                                                                       
##  [2] "as cat simply catenates streams of bytes, it can be also used to concatenate binary files, where it will just concatenate sequence of bytes"                                                                                         
##  [3] "a common interactive use of cat for a single file is to output the content of a file to standard output"
</code></pre>

<p>Next, we are going to create a list with all the words that once can find in each of the sentences contained in our dataset. What we aim to acquire is a list with all the unique words.</p>

<pre><code>
words_per_sentence <- c()
for(i in 1:length(lowcase_sentences)){
  a <- strsplit(lowcase_sentences[i], split = ' |,')
  words_per_sentence[i] <- a
}
words_per_sentence[[1:2]]

## [[1]]
##  [1] "in"            "comparison"    "to"            "dogs"         
##  [5] ""              "cats"          "have"          "not"          
##  [9] "undergone"     "major"         "changes"       "during"       
## [13] "the"           "domestication" "process"      
## 
## [[2]]
##  [1] "as"          "cat"         "simply"      "catenates"   "streams"    
##  [6] "of"          "bytes"       ""            "it"          "can"        
## [11] "be"          "also"        "used"        "to"          "concatenate"
## [16] "binary"      "files"       ""            "where"       "it"         
## [21] "will"        "just"        "concatenate" "sequence"    "of"         
## [26] "bytes" 
</code></pre>

<p>But before getting all the unique ones, as we did with the sentences, we are going to “unlist” the set of words and place them all in a vector.</p>

<pre><code>
all_the_words <- unlist(words_per_sentence, use.names = FALSE)
all_the_words

##   [1] "in"            "comparison"    "to"            "dogs"         
##   [5] ""              "cats"          "have"          "not"          
##   [9] "undergone"     "major"         "changes"       "during"       
##  [13] "the"           "domestication" "process"       "as"           
##  [17] "cat"           "simply"        "catenates"     "streams"      
##  [21] "of"            "bytes"         ""              "it"           
##  [25] "can"           "be"            "also"          "used"         
##  [29] "to"            "concatenate"   "binary"        "files"        
##  [33] ""              "where"         "it"            "will"         
##  [37] "just"          "concatenate"   "sequence"      "of"           
##  [41] "bytes"         "a"             "common"        "interactive"  
##  [45] "use"           "of"            "cat"           "for"          
##  [49] "a"             "single"        "file"          "is"           
##  [53] "to"            "output"        "the"           "content"      
##  [57] "of"            "a"             "file"          "to"           
##  [61] "standard"      "output"        "cats"          "can"          
##  [65] "hear"          "sounds"        "too"           "faint"        
##  [69] "or"            "too"           "high"          "in"           
##  [73] "frequency"     "for"           "human"         "ears"         
##  [77] ""              "such"          "as"            "those"        
##  [81] "made"          "by"            "mice"          "and"          
##  [85] "other"         "small"         "animals"       "in"           
##  [89] "one"           ""              "people"        "deliberately" 
##  [93] "tamed"         "cats"          "in"            "a"            
##  [97] "process"       "of"            "artificial"    "selection"    
## [101] ""              "as"            "they"          "were"         
## [105] "useful"        "predators"     "of"            "vermin"       
## [109] "the"           "domesticated"  "cat"           "and"          
## [113] "its"           "closest"       "wild"          "ancestor"     
## [117] "are"           "both"          "diploid"       "organisms"    
## [121] "that"          "possess"       "38"            "chromosomes"  
## [125] "and"           "roughly"       "20"            "000"          
## [129] "genes"         "domestic"      "cats"          "are"          
## [133] "similar"       "in"            "size"          "to"           
## [137] "the"           "other"         "members"       "of"           
## [141] "the"           "genus"         "felis"         ""             
## [145] "typically"     "weighing"      "between"       "4"            
## [149] "and"           "5"             "kg"            "(88"          
## [153] "and"           "110"           "lb)"           "however"      
## [157] ""              "if"            "the"           "output"       
## [161] "is"            "piped"         "or"            "redirected"   
## [165] ""              "cat"           "is"            "unnecessary"  
## [169] "cat"           "with"          "one"           "named"        
## [173] "file"          "is"            "safer"         "where"        
## [177] "human"         "error"         "is"            "a"            
## [181] "concern"       "-"             "one"           "wrong"        
## [185] "use"           "of"            "the"           "default"      
## [189] "redirection"   "symbol"        "\">\""         "instead"      
## [193] "of"            "\"<\""         "(often"        "adjacent"     
## [197] "on"            "keyboards)"    "may"           "permanently"  
## [201] "delete"        "the"           "file"          "you"          
## [205] "were"          "just"          "needing"       "to"           
## [209] "read"          "in"            "terms"         "of"           
## [213] "legibility"    ""              "a"             "sequence"     
## [217] "of"            "commands"      "starting"      "with"         
## [221] "cat"           "and"           "connected"     "by"           
## [225] "pipes"         "has"           "a"             "clear"        
## [229] "left-to-right" "flow"          "of"            "information"  
## [233] "cat"           "command"       "is"            "one"          
## [237] "of"            "the"           "basic"         "commands"     
## [241] "that"          "you"           "learned"       "when"         
## [245] "you"           "started"       "in"            "the"          
## [249] "unix"          "/"             "linux"         "world"        
## [253] "using"         "cat"           "command"       ""             
## [257] "the"           "lines"         "received"      "from"         
## [261] "stdin"         "can"           "be"            "redirected"   
## [265] "to"            "a"             "new"           "file"         
## [269] "using"         "redirection"   "symbols"       "when"         
## [273] "you"           "type"          "simply"        "cat"          
## [277] "command"       "without"       "any"           "arguments"    
## [281] ""              "it"            "just"          "receives"     
## [285] "the"           "stdin"         "content"       "and"          
## [289] "displays"      "it"            "in"            "the"          
## [293] "stdout"        "leopard"       "was"           "released"     
## [297] "on"            "october"       "26"            ""             
## [301] "2007"          "as"            "the"           "successor"    
## [305] "of"            "tiger"         "(version"      "104)"         
## [309] ""              "and"           "is"            "available"    
## [313] "in"            "two"           "editions"      "according"    
## [317] "to"            "apple"         ""              "leopard"      
## [321] "contains"      "over"          "300"           "changes"      
## [325] "and"           "enhancements"  "over"          "its"          
## [329] "predecessor"   ""              "mac"           "os"           
## [333] "x"             "tiger"         "as"            "of"           
## [337] "mid"           "2010"          ""              "some"         
## [341] "apple"         "computers"     "have"          "firmware"     
## [345] "factory"       "installed"     "which"         "will"         
## [349] "no"            "longer"        "allow"         "installation" 
## [353] "of"            "mac"           "os"            "x"            
## [357] "leopard"       "since"         "apple"         "moved"        
## [361] "to"            "using"         "intel"         "processors"   
## [365] "in"            "their"         "computers"     ""             
## [369] "the"           "osx86"         "community"     "has"          
## [373] "developed"     "and"           "now"           "also"         
## [377] "allows"        "mac"           "os"            "x"            
## [381] "tiger"         "and"           "later"         "releases"     
## [385] "to"            "be"            "installed"     "on"           
## [389] "non-apple"     "x86-based"     "computers"     "os"           
## [393] "x"             "mountain"      "lion"          "was"          
## [397] "released"      "on"            "july"          "25"           
## [401] ""              "2012"          "for"           "purchase"     
## [405] "and"           "download"      "through"       "apple's"      
## [409] "mac"           "app"           "store"         ""             
## [413] "as"            "part"          "of"            "a"            
## [417] "switch"        "to"            "releasing"     "os"           
## [421] "x"             "versions"      "online"        "and"          
## [425] "every"         "year"          "apple"         "has"          
## [429] "released"      "a"             "small"         "patch"        
## [433] "for"           "the"           "three"         "most"         
## [437] "recent"        "versions"      "of"            "safari"       
## [441] "running"       "on"            "os"            "x"            
## [445] "yosemite"      ""              "mavericks"     ""             
## [449] "and"           "mountain"      "lion"          "the"          
## [453] "mountain"      "lion"          "release"       "marks"        
## [457] "the"           "second"        "time"          "apple"        
## [461] "has"           "offered"       "an"            "incremental"  
## [465] "upgrade"       ""              "rather"        "than"         
## [469] "releasing"     "a"             "new"           "cat"          
## [473] "entirely"      "mac"           "os"            "x"            
## [477] "mountain"      "lion"          "installs"      "in"           
## [481] "place"         ""              "so"            "you"          
## [485] "won't"         "need"          "to"            "create"       
## [489] "a"             "separate"      "disk"          "or"           
## [493] "run"           "the"           "installation"  "off"          
## [497] "an"            "external"      "drive"         "the"          
## [501] "fifth"         "major"         "update"        "to"           
## [505] "mac"           "os"            "x"             ""             
## [509] "leopard"       ""              "contains"      "such"         
## [513] "a"             "mountain"      "of"            "features"     
## [517] "-"             "more"          "than"          "300"          
## [521] "by"            "apple's"       "count"
</code></pre>

<p>Aaah, we see that there are some empty indices contained in the vector. We are going to clean this vector a bit, and acquire therequested-unique-word vector.</p>

<pre><code>
no_numbers <- unique(removeNumbers(all_the_words))[unique(removeNumbers(all_the_words)) != ""]
clean_words <- removePunctuation(no_numbers)[removePunctuation(no_numbers) != ""]
clean_words

##   [1] "in"            "comparison"    "to"            "dogs"         
##   [5] "cats"          "have"          "not"           "undergone"    
##   [9] "major"         "changes"       "during"        "the"          
##  [13] "domestication" "process"       "as"            "cat"          
##  [17] "simply"        "catenates"     "streams"       "of"           
##  [21] "bytes"         "it"            "can"           "be"           
##  [25] "also"          "used"          "concatenate"   "binary"       
##  [29] "files"         "where"         "will"          "just"         
##  [33] "sequence"      "a"             "common"        "interactive"  
##  [37] "use"           "for"           "single"        "file"         
##  [41] "is"            "output"        "content"       "standard"     
##  [45] "hear"          "sounds"        "too"           "faint"        
##  [49] "or"            "high"          "frequency"     "human"        
##  [53] "ears"          "such"          "those"         "made"         
##  [57] "by"            "mice"          "and"           "other"        
##  [61] "small"         "animals"       "one"           "people"       
##  [65] "deliberately"  "tamed"         "artificial"    "selection"    
##  [69] "they"          "were"          "useful"        "predators"    
##  [73] "vermin"        "domesticated"  "its"           "closest"      
##  [77] "wild"          "ancestor"      "are"           "both"         
##  [81] "diploid"       "organisms"     "that"          "possess"      
##  [85] "chromosomes"   "roughly"       "genes"         "domestic"     
##  [89] "similar"       "size"          "members"       "genus"        
##  [93] "felis"         "typically"     "weighing"      "between"      
##  [97] "kg"            "lb"            "however"       "if"           
## [101] "piped"         "redirected"    "unnecessary"   "with"         
## [105] "named"         "safer"         "error"         "concern"      
## [109] "wrong"         "default"       "redirection"   "symbol"       
## [113] "instead"       "often"         "adjacent"      "on"           
## [117] "keyboards"     "may"           "permanently"   "delete"       
## [121] "you"           "needing"       "read"          "terms"        
## [125] "legibility"    "commands"      "starting"      "connected"    
## [129] "pipes"         "has"           "clear"         "lefttoright"  
## [133] "flow"          "information"   "command"       "basic"        
## [137] "learned"       "when"          "started"       "unix"         
## [141] "linux"         "world"         "using"         "lines"        
## [145] "received"      "from"          "stdin"         "new"          
## [149] "symbols"       "type"          "without"       "any"          
## [153] "arguments"     "receives"      "displays"      "stdout"       
## [157] "leopard"       "was"           "released"      "october"      
## [161] "successor"     "tiger"         "version"       "available"    
## [165] "two"           "editions"      "according"     "apple"        
## [169] "contains"      "over"          "enhancements"  "predecessor"  
## [173] "mac"           "os"            "x"             "mid"          
## [177] "some"          "computers"     "firmware"      "factory"      
## [181] "installed"     "which"         "no"            "longer"       
## [185] "allow"         "installation"  "since"         "moved"        
## [189] "intel"         "processors"    "their"         "osx"          
## [193] "community"     "developed"     "now"           "allows"       
## [197] "later"         "releases"      "nonapple"      "xbased"       
## [201] "mountain"      "lion"          "july"          "purchase"     
## [205] "download"      "through"       "apples"        "app"          
## [209] "store"         "part"          "switch"        "releasing"    
## [213] "versions"      "online"        "every"         "year"         
## [217] "patch"         "three"         "most"          "recent"       
## [221] "safari"        "running"       "yosemite"      "mavericks"    
## [225] "release"       "marks"         "second"        "time"         
## [229] "offered"       "an"            "incremental"   "upgrade"      
## [233] "rather"        "than"          "entirely"      "installs"     
## [237] "place"         "so"            "wont"          "need"         
## [241] "create"        "separate"      "disk"          "run"          
## [245] "off"           "external"      "drive"         "fifth"        
## [249] "update"        "features"      "more"          "count"
</code></pre>

<p>We see that there are 252 unique words in the the 22 sentences. Note that there are words like “x” or “lb” or “kg”. We are going to complete our analysis, including those words. One, later, can set different kind of restrictions in order to exclude all those abbreviations or symbols. Moving on, we are going to create a matrix with 22 lines (as the number of sentences) and 252 columns (as the number of unique words exist). What we aim to get is the number that each word appears in each sentence. For example, if the word cat is in the first sentence two times in the matrix’s cell [1,cat] (first row as for the sentence and cat’s column) we are going to see the number two. Off we go, we have the following code. Note that, due to the fact that the table is quite long we are going to show, only a small part of it. We can see the table, in your R studio, by using the following command: View(unique_mat).</p>

<pre><code>
unique_mat <- matrix(data = NA, nrow = length(sentences), ncol = length(clean_words))
for(i in 1:length(sentences)){
  for(j in 1:length(clean_words)){
    a <- sum(clean_words[j] == words_per_sentence[[i]])
    unique_mat[i,j] <- a
  }
}
unique_mat[1:10,1:10]

##       [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
##  [1,]    1    1    1    1    1    1    1    1    1     1
##  [2,]    0    0    1    0    0    0    0    0    0     0
##  [3,]    0    0    2    0    0    0    0    0    0     0
##  [4,]    1    0    0    0    1    0    0    0    0     0
##  [5,]    2    0    0    0    1    0    0    0    0     0
##  [6,]    0    0    0    0    0    0    0    0    0     0
##  [7,]    1    0    1    0    1    0    0    0    0     0
##  [8,]    0    0    0    0    0    0    0    0    0     0
##  [9,]    0    0    1    0    0    0    0    0    0     0
## [10,]    1    0    0    0    0    0    0    0    0     0
</code></pre>

<p>Now we are ready to use the matrix with all the unique words we just created in order to calculate the cosine distance of each sentence with the first one. In order to accomplish that we are going to use a for-loop.</p>

<pre><code>
distances <- c()
for(i in 1:(length(sentences))){
  a <- cosine(x = unique_mat[1,], y = unique_mat[i,])
  distances[i] <- a
}
distances

##  [1] 1.00000000 0.04724556 0.13552619 0.10482848 0.22291129 0.05976143
##  [7] 0.27277236 0.07412493 0.11821656 0.04962917 0.16718346 0.11952286
## [13] 0.16035675 0.13363062 0.12598816 0.05572782 0.17817416 0.04454354
## [19] 0.05572782 0.11145564 0.16366342 0.18394180

cosine_test <- c()
for(i in 1:(length(sentences))){
  a <- (sum(unique_mat[1,]*unique_mat[i,]))/(length(unique_mat[1,])*length(unique_mat[i,]))
  cosine_test[i] <- a
}
which(cosine_test == min(cosine_test))

## [1]  2  6  8 10 16 18 19

cosine_test

##  [1] 2.204586e-04 1.574704e-05 4.724112e-05 3.149408e-05 6.298816e-05
##  [6] 1.574704e-05 7.873520e-05 1.574704e-05 4.724112e-05 1.574704e-05
## [11] 4.724112e-05 3.149408e-05 4.724112e-05 3.149408e-05 3.149408e-05
## [16] 1.574704e-05 6.298816e-05 1.574704e-05 1.574704e-05 3.149408e-05
## [21] 4.724112e-05 4.724112e-05

#2nd option to calculate it
cosine_test2 <- c()
for(i in 1:(length(sentences))){
  a <- (unique_mat[1,]%*%unique_mat[i,])/(length(unique_mat[1,])*length(unique_mat[i,]))
  cosine_test2[i] <- a
}
</code></pre>

<p>Well, in this case, we can see that we only have 22 sentences but we will follow the assumption that we can not compare 22 numbers. So we have to figure the ones that are most and least similar to the first one.</p>

<pre><code>
min(distances, na.rm = TRUE); max(distances[2:length(distances)], na.rm = TRUE)

## [1] 0.04454354

## [1] 0.2727724

cat(which(min(distances, na.rm = TRUE) == distances), "-", min(distances, na.rm = TRUE),"\n", which(max(distances[2:length(distances)], na.rm = TRUE) == distances), "-", max(distances[2:length(distances)], na.rm = TRUE))

## 18 - 0.04454354 
##  7 - 0.2727724
</code></pre>

<p>So what we see from the results presented above is that the 18th sentence is the one that is the least similar and the 7th one the most similar to the first one. However the objective is to find the two sentences that are the most similar to the first one. To do that, we are going to use the function that we created in the beginning of this project. This function is called (as you probable have already seen) nr_values and works as follows. The arguments that this function needs in order to operate properly are a distance vector (in our case distances), the number of instances required and if you want to see the most or least similar to the first one. When I am saying number of instances, I mean the following (I am going to explain this with an example). We need the two sentences that are the most similar to the first one, so in our case the number of instances is two. As a result:</p>

<pre><code>
nr_values(dist_val = distances, number = 2, type = "most")

## 0.2727724 ( 7 ) 
## 0.2229113 ( 5 )
</code></pre>

<p>So we see that the seventh and the fifth sentences are the ones that are most similar with the first one. The sentences are the following: </p>

<p>In one, people diliberately tamed cats in a process of artificial selection, as they were useful predators of vermin.</p>

<p>Domestic cats are similar in size to the other members of the genus Felis, typically weighting between 4 and 5 kg (8.8 and 11.0 lb).</p>

<p>Now let us see what a machine learning algorithm gives us as result to our similarity problem.</p>

<pre><code>
distance_mat <- dist.cosine(x = unique_mat)

hs_wardD2 <- hclust(distance_mat, method = "ward.D2")

plot(hs_wardD2, hang = -1, xlab = "Similarity Clusters")
</code></pre>

<p>As you can see according to Hierarchical Clustering algorithm, the first sentence has been grouped with the fourth one. Seventh sentence is in the same group if we use 4 clusters, though the fifth one is not. This does not agree with our previous results. Here we have presented two different ways of calculating the similarity between sentences, and we all became familiar with the process of finding the sentences (or documents, in a larger scale) that are most similar to the one we want to compare to. The question at this point is what is your guess from the beginning. Do you agree with the analytic process or the ML algorithm?</p>

<p>I hope you enjoyed this analysis, as much as I did. Hopefully you have gained some useful information, and will return in the future to copy some part of it and use it for your own analysis.</p>

<hr>
<p>Be safe, code safer!</p>