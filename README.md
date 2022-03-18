# pymol_methods


Since python 3,  scripts used prior for mapping in pymol don't work...instead install pymol version 2.5 in a conda environment:

              conda create -n test_pymol -c tpeulen -c conda-forge pymol-open-source
              conda activate test_pymol
              conda install -c conda-forge pmw # if don't have pmw already for py2.7
              pymol 



see here: https://github.com/schrodinger/pymol-open-source/issues/110



You will need the abps plugin (can download from here: https://pymolwiki.org/index.php/Apbsplugin )



# Mapping data to structures in pymol 

1. Save data as tab delimited file and find minimum and maximum values.

    e.g test.txt
    1   0.01
    2   0.21
    3   0.99

2. Download  data2bfactor.py and spectrumany.py save to working dir (FINAL_PYMOL).

3. Load pdb structure in pymol.

4. Run data2bfactor script in pymol commandline 

        PYMOL> run /home/path/to/data2bfactor.py

5.Run spectrumany script in pymol commandline:

        PYMOL> run /home/path/to/spectrumany.py
      
6. Run spectrumany script in pymol commandline
7. 
        PYMOL> run /home/path/to/spectrum_bar.py

7.Select region, chain or entire molecule to add data info to:

e.g full model select : 

        PYMOL> select  model.pdb

(see http://betainverse.github.io/blog/2014/10/13/pymol-color-by-data/  for more options)

8.Run data2b function:

        data2b_res model.pdb, /home/path/to/test.txt

9.Run spectrum function (using min and max values for colour gradient)

        spectrum b, rainbow, model.test, minimum=-1.04, maximum=1.37
        
(see https://pymolwiki.org/index.php/Spectrumbar)


10.Run spectrumany to edit spectrum colours (using min and max values again):

        spectrumany b, purple grey80, model.pdb, minimum=-0.01,maximum=1.4

      
Notes:

e.g Colour everything below 0.7  

        spectrumany b, cyan purple, model.pdb, minimum=0.7,maximum=1.37



PYMOL ADD COLOUR BAR

        ramp_new colorbar, none, [-1.4, 1.37], [cyan, purple]
        ramp_new colorbar, none, [0.7, 1.37], [cyan, purple]
        OR :
        spectrumbar red,orange,yellow,green,blue,purple


## Manual selections for sites: 

pymol manual colouring:
https://bioinformatics.stackexchange.com/questions/2859/how-to-colour-multiple-residues-in-pymol

        select toBeColored, ((i. 10-20 or i. 30-40) and c. L ) or ((i. 5-10+20-30) and c. H)
        color yellow, toBeColored

