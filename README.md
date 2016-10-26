# lynis_report
[![Build Status](https://travis-ci.org/d4t4king/lynis_report.svg?branch=master)](https://travis-ci.org/d4t4king/lynis_report)

Manageable report from lynis text output. Currently available report formats: HTML, PDF, Microsoft Excel (XLSX)\*.

If you want to be able to use the PDF or Excel output formats, you must install some additional software.  As is, the modules are required regardless of whether you use these features or not.  Attempts are being made to change that behavior.

## Instriuctions for pre-requisite installation:

### For Debian/Ubuntu
```
(as root)
apt update							# versions prior to 16.04 LTS should use 'apt-get'
apt -y install htmldoc

pushd /tmp/
wget http://search.cpan.org/CPAN/authors/id/M/MF/MFRANKL/HTML-HTMLDoc-0.10.tar.gz
tar xvf HTML-HTMLDoc-0.10.tar.gz
pushd HTML-HTMLDoc-0.10
perl Makefile.PL
make && make install
popd
wget http://search.cpan.org/CPAN/authors/id/J/JM/JMCNAMARA/Excel-Writer-XLSX-0.95.tar.gz
tar xvf Excel-Writer-XLSX-0.95.tar.gz
pushd Excel-Writer-XLSX-0.95
perl Makefile.PL
make && make install
popd
popd
```
### For RHEL/CentOS/Fedora
```
(as root)
yum -y install htmldoc perl-Excel-Writer-XLSX
pushd /tmp/
wget http://search.cpan.org/CPAN/authors/id/M/MF/MFRANKL/HTML-HTMLDoc-0.10.tar.gz
tar xvf HTML-HTMLDoc-0.10.tar.gz
pushd HTML-HTMLDoc-0.10
perl Makefile.PL
make && make install
popd
popd
```

### for Gentoo
```
(as root)
emerge -av1 app-text/htmldoc dev-perl/HTML-HTMLDoc 

pushd /tmp/
wget http://search.cpan.org/CPAN/authors/id/J/JM/JMCNAMARA/Excel-Writer-XLSX-0.95.tar.gz
tar xvf Excel-Writer-XLSX-0.95.tar.gz
pushd Excel-Writer-XLSX-0.95
perl Makefile.PL
make && make install
popd
popd
```


\* It's possible that the Excel format will load for LibreOffic Calc, but this is currentl untested.  YMMV.

## Help Statement
```
./lynis_report.pl -h|--help -v|--verbose -E|--excel -o|--output

Where:

-h|--help                       Display this useful message, then exit.
-v|--verbose                    Display more detailed output.  This is typically used for
                                debugging, but may provide insight when running into problems.
-E|--excel                      Output the report in Microsoft Excel binary format.  This
                                options is not yet implemented (NYI).
-o|--output                     Specifies the output file to print the report to.
```
* HTML out features (default)
	* Summarizes the lynis report into a single HTML file.
* Excel out features
	* Breaks out sections into worksheets.
* PDF out features
	* Copy of the HTML report ported to PDF.


## TODO:
* PDF out needs refinement
* Other output formats?
