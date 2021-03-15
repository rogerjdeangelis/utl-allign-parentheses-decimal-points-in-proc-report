# utl-allign-parentheses-decimal-points-in-proc-report
Allign parentheses decimal points in proc report

    Allign parentheses decimal points in proc report

    Many fonts use fixed spacing(nonospace) for digits

    I like to use Verdana font

       PROBLEM

             INPUT                   OUTPUT

          10/10000(0.1%)        10/10000 (   0.1%)
          1/100(1.0%)           1/100    (   1.0%)
          100/100(100.0%)       100/100  ( 100.0%)



    GitHub
    https://tinyurl.com/rth79c98
    https://github.com/rogerjdeangelis/utl-allign-parentheses-decimal-points-in-proc-report

    Inspired by
    https://tinyurl.com/aydy2kec
    https://communities.sas.com/t5/SAS-Programming/allign-parentheses-decimal-points-in-proc-report/m-p/725772

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;
    data have;
      retain name "John";
      length cntPct $25.;
      input ;
      top=scan(_infile_,1,'(');
      pct=scan(_infile_,2,'(');
      cntPct=put(top,$8. -l)!!" "!!"("!!put(pct,$8. -r);
    cards4;
    11/111(11.1%)
    00/000(00.0%)
    10/100(10.0%)
    100/1000(10.0%)
    10/10000(0.1%)
    1/100(1.0%)
    100/100(100.0%)
    ;;;;
    run;quit;

    ods rtf file="d:/rtf/want.rtf";
    proc report data=have nowd missing;
    title "Allign parentheses decimal points in proc report";
    cols name cntPct;
    define cntPct / display right style={font_face=verdana cellwidth=3in};
    run;quit;
    ods rtf close;

    *            _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| '_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    ;

    * Output in the rtf ;

    Allign parentheses decimal points in proc report

      NAME                     CNTPCT

      John         11/111   (  11.1%)
      John         00/000   (  00.0%)
      John         10/100   (  10.0%)
      John         100/1000 (  10.0%)
      John         10/10000 (   0.1%)
      John         1/100    (   1.0%)
      John         100/100  ( 100.0%)




