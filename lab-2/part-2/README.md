# Substitution Cipher

## Code

```cpp
#include<bits/stdc++.h>
using namespace std;

bool cmp(const pair<char,double>& x, const pair<char,double>& y) {
    return x.second > y.second;  // Use strict greater to ensure stable sort behavior
}

int main() {
    freopen("input.txt","r",stdin);
    freopen("output.txt","w",stdout);
    vector<string> cipherArray;
    string cipher;
    map<char,int> freq;

    for( char ch = 'a'; ch <= 'z'; ch++ ) {
        freq[ch] = 0;
    }

    int count = 0;
    while(getline(cin,cipher)) {
	// Convert line to lowercase
        transform(cipher.begin(), cipher.end(), cipher.begin(), ::tolower);
        for(char c : cipher) {
            if (isalpha(c)) {
                count++;
                freq[c]++;
            }
        }
        cipherArray.push_back(cipher);
    }

    vector<pair<char,double>> cipherFreq, plainFreq;
    cout << "--------- cipher letter Frequency ----------" << endl;
    for(auto it : freq) {
        double percentage = double(it.second * 100.00) / double(count);
        cout << it.first << "  " << fixed << setprecision(2) << percentage << "%" << endl;
        cipherFreq.push_back({it.first, percentage});
    }

    map<char, double> freqDist = {
        {'a', 8.05}, {'b', 1.67}, {'c', 2.23}, {'d', 5.1}, {'e', 12.22},
        {'f', 2.14}, {'g', 2.3}, {'h', 6.62}, {'i', 6.28}, {'j', 0.19},
        {'k', 0.95}, {'l', 4.08}, {'m', 2.33}, {'n', 6.95}, {'o', 7.63},
        {'p', 1.66}, {'q', 0.06}, {'r', 5.29}, {'s', 6.02}, {'t', 9.67},
        {'u', 2.92}, {'v', 0.82}, {'w', 2.6}, {'x', 0.11}, {'y', 2.04},
        {'z', 0.06}
    };

    cout << "--------- plain letter Frequency ----------" << endl;
    for(auto it : freqDist) {
        cout << it.first << "  " << fixed << setprecision(2) << it.second << "%" << endl;
        plainFreq.push_back({it.first, it.second});
    }

    sort(plainFreq.begin(), plainFreq.end(), cmp);
    sort(cipherFreq.begin(), cipherFreq.end(), cmp);

    map<char, char> charMap;
    cout << "--------- frequency compare ----------" << endl;
    for(int i = 0; i < 26; i++) {
        cout << cipherFreq[i].first << " -> " << plainFreq[i].first << endl;
        charMap[cipherFreq[i].first] = plainFreq[i].first;
    }

    cout << "--------- Decoding ----------" << endl;
    for(auto& line : cipherArray) {
        for(char& c : line) {
            if (isalpha(c)) {
                c = charMap[c];
            }
        }
        cout << line << endl;
    }

    return 0;
}
```

## Output

### Test Case 01

### input.txt

	af p xpkcaqvnpk pfg, af ipqe qpri, gauuikifc tpw, ceiri udvk tiki afgarxifrphni cd eao-
	-wvmd popkwn, hiqpvri du ear jvaql vfgikrcpfgafm du cei xkafqaxnir du xrwqedearcdkw pfg
	du ear aopmafpcasi xkdhafmr afcd fit pkipr. ac tpr qdoudkcafm cd lfdt cepc au pfwceafm
	epxxifig cd ringdf eaorinu hiudki cei opceiopcaqr du cei uaing qdvng hi qdoxnicinw tdklig dvc-
	-pfg edt rndtnw ac xkdqiigig, pfg edt odvfcpafdvr cei dhrcpqnir--ceiki tdvng pc niprc kiopaf dfi
	mddg oafg cepc tdvng qdfcafvi cei kiripkqe

### output.txt

	--------- cipher letter Frequency ----------
	a  3.04%
	b  0.26%
	c  6.59%
	d  1.87%
	e  4.59%
	f  0.00%
	g  1.81%
	h  7.30%
	i  0.00%
	j  4.78%
	k  8.53%
	l  6.27%
	m  6.14%
	n  2.39%
	o  8.47%
	p  1.42%
	q  2.71%
	r  0.45%
	s  2.46%
	t  2.20%
	u  12.80%
	v  5.49%
	w  2.46%
	x  0.00%
	y  1.81%
	z  6.14%
	--------- plain letter Frequency ----------
	a  8.05%
	b  1.67%
	c  2.23%
	d  5.10%
	e  12.22%
	f  2.14%
	g  2.30%
	h  6.62%
	i  6.28%
	j  0.19%
	k  0.95%
	l  4.08%
	m  2.33%
	n  6.95%
	o  7.63%
	p  1.66%
	q  0.06%
	r  5.29%
	s  6.02%
	t  9.67%
	u  2.92%
	v  0.82%
	w  2.60%
	x  0.11%
	y  2.04%
	z  0.06%
	--------- frequency compare ----------
	u -> e
	k -> t
	o -> a
	h -> o
	c -> n
	l -> h
	z -> i
	m -> s
	v -> r
	j -> d
	e -> l
	a -> u
	q -> w
	w -> m
	s -> g
	n -> c
	t -> f
	d -> y
	g -> b
	y -> p
	p -> k
	r -> v
	b -> j
	i -> x
	f -> q
	x -> z
	--------- Decoding ----------
	unluo fai kerb rnyh asd kerb peywlnar, asd had uees the fosder og the ihnre gor
	injtb beari, eker insye hni remarvaule dniappearasye asd wsejpeyted retwrs. the
	rnyhei he had urowcht uayv grom hni trakeli had sof ueyome a loyal lecesd, asd nt fai
	popwlarlb uelneked, fhateker the old golv mncht iab, that the hnll at uac esd fai gwll og
	twsseli itwgged fnth treaiwre. asd ng that fai sot esowch gor game, there fai alio hni
	prolosced kncowr to markel at. tnme fore os, uwt nt ieemed to hake lnttle eggeyt os
	mr. uaccnsi. at snsetb he fai mwyh the iame ai at gngtb. at snsetb-snse theb uecas to
	yall hnm fell-preierked; uwt wsyhasced fowld hake uees searer the marv. there fere iome
	that ihoov thenr headi asd thowcht thni fai too mwyh og a cood thnsc; nt ieemed wsganr that
	asbose ihowld poiieii (apparestlb) perpetwal bowth ai fell ai (repwtedlb)
	nsejhawitnule fealth. nt fnll hake to ue pand gor, theb iand. nt nis't satwral, asd trowule
	fnll yome og nt! uwt io gar trowule had sot yome; asd ai mr. uaccnsi fai ceserowi fnth
	hni moseb, moit people fere fnllnsc to gorcnke hnm hni oddntnei asd hni cood gortwse. he
	remansed os knintnsc termi fnth hni relatnkei (ejyept, og yowrie, the iayvknlle-
	uaccnsiei), asd he had masb dekoted admnreri amosc the houunti og poor asd
	wsnmportast gamnlnei. uwt he had so yloie grnesdi, wstnl iome og hni bowscer yowinsi
	uecas to crof wp. the eldeit og theie, asd unluo'i gakowrnte, fai bowsc grodo uaccnsi.
	fhes unluo fai snsetb-snse he adopted grodo ai hni henr, asd urowcht hnm to lnke at uac
	esd; asd the hopei og the iayvknlle- uaccnsiei fere gnsallb daihed. unluo asd grodo
	happesed to hake the iame unrthdab, ieptemuer 22sd. bow had uetter yome asd lnke here,
	grodo mb lad, iand unluo ose dab; asd thes fe yas yeleurate owr unrthdab-partnei
	yomgortaulb tocether. at that tnme grodo fai itnll ns hni tfeesi, ai the houunti yalled the
	nrreiposinule tfestnei uetfees yhnldhood asd yomnsc og ace at thnrtb-three

### Test Case 02

#### input.txt

	aceah toz puvg vcdl omj puvg yudqecov, omj loj auum klu thmjuv hs klu zlcvu shv
	zcbkg guovz, upuv zcmdu lcz vuwovroaeu jczoyyuovomdu omj qmubyudkuj vukqvm. klu
	vcdluz lu loj avhqnlk aodr svhw lcz kvopuez loj mht audhwu o ehdoe eunumj, omj ck toz
	yhyqeoveg auecupuj, tlokupuv klu hej sher wcnlk zog, klok klu lcee ok aon umj toz sqee hs
	kqmmuez zkqssuj tckl kvuozqvu. omj cs klok toz mhk umhqnl shv sowu, kluvu toz oezh lcz
	yvhehmnuj pcnhqv kh wovpue ok. kcwu thvu hm, aqk ck zuuwuj kh lopu eckkeu ussudk hm
	wv. aonncmz. ok mcmukg lu toz wqdl klu zowu oz ok scskg. ok mcmukg-mcmu klug aunom kh
	doee lcw tuee-yvuzuvpuj; aqk qmdlomnuj thqej lopu auum muovuv klu wovr. kluvu tuvu zhwu
	klok zlhhr klucv luojz omj klhqnlk klcz toz khh wqdl hs o nhhj klcmn; ck zuuwuj qmsocv klok
	omghmu zlhqej yhzzuzz (oyyovumkeg) yuvyukqoe ghqkl oz tuee oz (vuyqkujeg)
	cmubloqzkcaeu tuoekl. ck tcee lopu kh au yocj shv, klug zocj. ck czm'k mokqvoe, omj kvhqaeu
	tcee dhwu hs ck! aqk zh sov kvhqaeu loj mhk dhwu; omj oz wv. aonncmz toz numuvhqz tckl
	lcz whmug, whzk yuhyeu tuvu tceecmn kh shvncpu lcw lcz hjjckcuz omj lcz nhhj shvkqmu. lu
	vuwocmuj hm pczckcmn kuvwz tckl lcz vueokcpuz (ubduyk, hs dhqvzu, klu zodrpceeu-
	aonncmzuz), omj lu loj womg juphkuj ojwcvuvz owhmn klu lhaackz hs yhhv omj
	qmcwyhvkomk sowcecuz. aqk lu loj mh dehzu svcumjz, qmkce zhwu hs lcz ghqmnuv dhqzcmz
	aunom kh nvht qy. klu uejuzk hs kluzu, omj aceah'z sophqvcku, toz ghqmn svhjh aonncmz.
	tlum aceah toz mcmukg-mcmu lu ojhykuj svhjh oz lcz lucv, omj avhqnlk lcw kh ecpu ok aon
	umj; omj klu lhyuz hs klu zodrpceeu- aonncmzuz tuvu scmoeeg jozluj. aceah omj svhjh
	loyyumuj kh lopu klu zowu acvkljog, zuykuwauv 22mj. ghq loj aukkuv dhwu omj ecpu luvu,
	svhjh wg eoj, zocj aceah hmu jog; omj klum tu dom dueuavoku hqv acvkljog-yovkcuz
	dhwshvkoaeg khnukluv. ok klok kcwu svhjh toz zkcee cm lcz ktuumz, oz klu lhaackz doeeuj klu
	cvvuzyhmzcaeu ktumkcuz auktuum dlcejlhhj omj dhwcmn hs onu ok klcvkg-klvuu

#### output.txt

	--------- cipher letter Frequency ----------
	a  3.03814%
	b  0.26%
	c  6.59%
	d  1.87%
	e  4.59%
	f  0.00%
	g  1.81%
	h  7.30%
	i  0.00%
	j  4.78%
	k  8.53%
	l  6.27%
	m  6.14%
	n  2.39%
	o  8.47%
	p  1.42%
	q  2.71%
	r  0.45%
	s  2.46%
	t  2.20%
	u  12.80%
	v  5.49%
	w  2.46%
	x  0.00%
	y  1.81%
	z  6.14%
	--------- plain letter Frequency ----------
	a  8.05 %
	b  1.6700 %
	c  2.2300 %
	d  5.1000 %
	e  12.2200 %
	f  2.1400 %
	g  2.3000 %
	h  6.6200 %
	i  6.2800 %
	j  0.1900 %
	k  0.9500 %
	l  4.0800 %
	m  2.3300 %
	n  6.9500 %
	o  7.6300 %
	p  1.6600 %
	q  0.0600 %
	r  5.2900 %
	s  6.0200 %
	t  9.6700 %
	u  2.9200 %
	v  0.8200 %
	w  2.6000 %
	x  0.1100 %
	y  2.0400 %
	z  0.0600 %
	--------- frequency compare ----------
	u -> e
	k -> t
	o -> a
	h -> o
	c -> n
	l -> h
	m -> i
	z -> s
	v -> r
	j -> d
	e -> l
	a -> u
	q -> w
	s -> m
	w -> g
	n -> c
	t -> f
	d -> y
	y -> b
	g -> p
	p -> k
	r -> v
	b -> j
	x -> x
	f -> z
	i -> q
	--------- Decoding ----------
	unluo fas kerp rnyh aid kerp beywlnar, aid had ueei the foider om the shnre mor
	snjtp pears, eker sniye hns regarvaule dnsabbearaiye aid wiejbeyted retwri. the
	rnyhes he had urowcht uayv mrog hns trakels had iof ueyoge a loyal leceid, aid nt fas
	bobwlarlp uelneked, fhateker the old molv gncht sap, that the hnll at uac eid fas mwll om
	twiiels stwmmed fnth treaswre. aid nm that fas iot eiowch mor mage, there fas also hns
	broloiced kncowr to garkel at. tnge fore oi, uwt nt seeged to hake lnttle emmeyt oi
	gr. uaccnis. at inietp he fas gwyh the sage as at mnmtp. at inietp-inie thep uecai to
	yall hng fell-breserked; uwt wiyhaiced fowld hake ueei iearer the garv. there fere soge
	that shoov thenr heads aid thowcht thns fas too gwyh om a cood thnic; nt seeged wimanr that
	aipoie showld bossess (abbareitlp) berbetwal powth as fell as (rebwtedlp)
	niejhawstnule fealth. nt fnll hake to ue band mor, thep sand. nt nsi't iatwral, aid trowule
	fnll yoge om nt! uwt so mar trowule had iot yoge; aid as gr. uaccnis fas ceierows fnth
	hns goiep, gost beoble fere fnllnic to morcnke hng hns oddntnes aid hns cood mortwie. he
	reganied oi knsntnic tergs fnth hns relatnkes (ejyebt, om yowrse, the sayvknlle-
	uaccnises), aid he had gaip dekoted adgnrers agoic the houunts om boor aid
	wingbortait magnlnes. uwt he had io ylose mrneids, witnl soge om hns powicer yowsnis
	uecai to crof wb. the eldest om these, aid unluo's makowrnte, fas powic mrodo uaccnis.
	fhei unluo fas inietp-inie he adobted mrodo as hns henr, aid urowcht hng to lnke at uac
	eid; aid the hobes om the sayvknlle- uaccnises fere mniallp dashed. unluo aid mrodo
	habbeied to hake the sage unrthdap, sebteguer 22id. pow had uetter yoge aid lnke here,
	mrodo gp lad, sand unluo oie dap; aid thei fe yai yeleurate owr unrthdap-bartnes
	yogmortaulp tocether. at that tnge mrodo fas stnll ni hns tfeeis, as the houunts yalled the
	nrresboisnule tfeitnes uetfeei yhnldhood aid yognic om ace at thnrtp-three

## Conclusion

The frequency analysis wasn’t proved fairly effective for these ciphertexts, because the accuracy of decoding can vary based on how closely the letter frequency in the ciphertext matches given English frequencies. 
