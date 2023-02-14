# Week 3 Lab Report

## Interesting command-line options for ```grep``` command

1. ```grep -r``` or ```grep --recursive```<br>
By applying this option, grep will go over all files under given directory and subdirectories recursively. However, it will ignore symlinks. This command is useful because we don't need to first use either find or some other command to first list all files before using grep.<br>
    - In the following code block, the command is trying to find all files containing string "Bahamas" under current directory and subdirectories.
    ```
    [name@ieng6-201]:skill-demo1-data:343$ grep -r "Bahamas" .
    Binary file ./.git/index matches
    ./written_2/travel_guides/berlitz1/WhatToFWI.txt:        waters off the Bahamas, Puerto Rico, and the Virgin Islands, but the
    ./written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
    ./written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.

    #and more...
    ```
    - In the following code block, the command is trying to find all files containing string "Haha" under current directory and subdirectories.
    ```
    [name@ieng6-201]:skill-demo1-data:344$ grep -r "Haha" .
    ./written_2/non-fiction/OUP/Kauffman/ch6.txt:Do you think you could finitely prestate all the context-dependent causal consequences of human artifacts that might turn out to be useful in some odd environment or for some odd purpose? I don’t think so. It is not that we cannot finitely prestate some infinite things. For example, Fourier had a wonderful idea. “Sine and cosines, you know,” he muttered to himself in French. “All possible wavelengths, out to infinity, down to infinitesimal, all possible phase oVsets.   .   .   . Haha!” And Fourier proved his theorem that any wiggly line on a plane surface could be approximated to arbitrary accuracy with a weighted set of phase-oVset sines and cosines drawn from the infinite basis set of all sine and cosine functions. Fourier finitely prestated an infinite basis set for all continuous diVerentiable wiggly lines on long blackboards.
    ```

2. ```grep -n``` or ```grep --line-number```<br>
By applying this option, grep will not only out put the context of the matched string but also where (or which line) it is. It will be super useful when we not only want to know which file contains that string but also want to know where the string is.<br>
    - In the following code block, the command is trying to find all files containing string "Haha" under current directory and subdirectories and show the position.
    ```
    [name@ieng6-201]:skill-demo1-data:346$ grep -n -r "Haha" .
    ./written_2/non-fiction/OUP/Kauffman/ch6.txt:91:Do you think you could finitely prestate all the context-dependent causal consequences of human artifacts that might turn out to be useful in some odd environment or for some odd purpose? I don’t think so. It is not that we cannot finitely prestate some infinite things. For example, Fourier had a wonderful idea. “Sine and cosines, you know,” he muttered to himself in French. “All possible wavelengths, out to infinity, down to infinitesimal, all possible phase oVsets.   .   .   . Haha!” And Fourier proved his theorem that any wiggly line on a plane surface could be approximated to arbitrary accuracy with a weighted set of phase-oVset sines and cosines drawn from the infinite basis set of all sine and cosine functions. Fourier finitely prestated an infinite basis set for all continuous diVerentiable wiggly lines on long blackboards.
    ```
    - In the following code block, the command is trying to find all files containing string "Beautiful" under current directory and subdirectories and show the position.
    ```
    [name@ieng6-201]:skill-demo1-data:347$ grep -n -r "Beautiful" .
    ./written_2/non-fiction/OUP/Castro/chM.txt:77:Mexico Lindo (Beautiful Mexico)
    ./written_2/travel_guides/berlitz1/HandRIsrael.txt:35:        rooms, many with wonderful views across the Gulf of Aqaba. Beautiful
    ./written_2/travel_guides/berlitz1/HandRJamaica.txt:74:        <www.halfmoon.com.jm>. Beautifully landscaped gardens and a
    ./written_2/travel_guides/berlitz1/WhatToEdinburgh.txt:268:        Beautiful examples of enamelware, ceramics, and pottery are produced in
    ./written_2/travel_guides/berlitz1/WhatToJamaica.txt:620:        tropical vegetation reach out into the ocean. Beautiful private villas
    ./written_2/travel_guides/berlitz1/WhatToMallorca.txt:178:        Beautifully landscaped Son Vida Golf (Tel. 971/79 12 10) hosts the
    ./written_2/travel_guides/berlitz1/WhereToFWI.txt:422:        Beautiful beaches lure the determined few off the beaten
    ./written_2/travel_guides/berlitz1/WhereToGreek.txt:707:        accumulated by the monastery. Beautifully displayed are a range of
    ./written_2/travel_guides/berlitz1/WhereToIbiza.txt:494:        Beautiful sandy beaches like Platja de Mitjorn go on for miles. Here
    ./written_2/travel_guides/berlitz1/WhereToIndia.txt:233:        the palace apartments on the Yamuna river. Beautiful as it is, with
    ./written_2/travel_guides/berlitz1/WhereToIsrael.txt:31:        Beautifully restored and with lush archaeological gardens, its towers
    ./written_2/travel_guides/berlitz1/WhereToIstanbul.txt:1038:        Izmir” (Beautiful Izmir), Turkey’s third-largest city sprawls around
    
    # and more...
    ```

3. ```grep -q``` or ```grep --quiet``` or ```grep --silent```<br>
By applying this option, normal output will be suppressed. The command will end immediately after execution with exit code 0 if there is at least one file containing matched string. If no matchings are found, the exit code will be 1. This will be usefule if we want to determine if the given file contains a certain string. <br>
    - In the following code block, the command is trying to determine if the file ```./written_2/non-fiction/OUP/Kauffman/ch6.txt``` contains string "Haha" or not. Exit code 0 means the answer is yes.
    ```
    [name@ieng6-201]:skill-demo1-data:358$ grep -q "Haha" ./written_2/non-fiction/OUP/Kauffman/ch6.txt
    [name@ieng6-201]:skill-demo1-data:359$ echo $?
    0
    ```
    - In the following code block, the command is trying to determine if the file ```./written_2/non-fiction/OUP/Kauffman/ch6.txt``` contains string "qwert" or not. Exit code 1 means the answer is no.
    ```
    [name@ieng6-201]:skill-demo1-data:360$ grep -q "qwert" ./written_2/non-fiction/OUP/Kauffman/ch6.txt
    [name@ieng6-201]:skill-demo1-data:361$ echo $?
    1
    ```

4. ```grep -e``` or ```grep --regexp```<br>
By applying this option, grep will interpret the input string as a regular expression. This will be extremely useful when we are trying to match strings with a certain pattern (e.g. email address). However, I cannot come up with a good use on given dataset.
    - In the following code block, the command is trying to find files containing email address like strings. As expected, we cannot find any.
    ```
    [name@ieng6-201]:skill-demo1-data:364$ grep -q -r -e "[a-zA-Z0-9._] +@ [a-zA-Z]+. [a-zA-Z]+" .
    [name@ieng6-201]:skill-demo1-data:365$ echo $?
    1
    ```
    - In the following code block, the command is trying to find files containing standard 10-digit phone number like strings.
    ```
    [name@ieng6-201]:skill-demo1-data:368$ grep -r -e "\(\(([0-9]\{3\})\|[0-9]\{3\}\)[ -]\?\)\{2\}[0-9]\{4\}" .
    ./written_2/non-fiction/OUP/Berk/ch7.txt:Because of wide individual differences, it’s sometimes hard to tell a language disorder from normal variation in language development. If you’re concerned about your child’s language progress, consult a trained speech–language pathologist. The American Speech–Language–Hearing Association (ASHA) maintains a list of certiﬁed speech–language pathologists for referrals. You can contact the association at (800) 638-8255.
    ./written_2/travel_guides/berlitz1/HandRHawaii.txt:        96815; Tel. (808) 922-2700 or (800) 336-5599; fax (808) 922-8785;
    ./written_2/travel_guides/berlitz1/HandRHawaii.txt:        (808) 923-2311 or (800) 367-2343; fax (808) 926-8004;
    ./written_2/travel_guides/berlitz1/HandRHawaii.txt:        HI 96815; Tel. (808) 949-4321 or (800) 445-8667; fax (808) 947-7898;

    #and more...
    ```