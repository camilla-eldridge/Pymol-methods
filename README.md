# pymol-methods


Scripts for mapping in pymol are for py2.7 (note - i'm not the script author)...now pymol uses py3 the work around is this:

To install pymol version 2.0 -2.4 in a conda environment:

            conda create -n pymol_py2.7 python=2.7   # make env for py2.7 
            conda activate pymol_py2.7
            conda install -c schrodinger pymol    #install older version on pymol in your 2.7 env 
            pymol


Just to note....to install the new pymol version 2.5 in a conda environment(note mapping scripts won't work with this version - for this method didn't use this version!!!!):

              conda create -n test_pymol -c tpeulen -c conda-forge pymol-open-source
              conda activate test_pymol
              conda install -c conda-forge pmw # if don't have pmw already for py2.7
              pymol 



The -c tells conda to install from the specified channel (channel=a location where packages are stored), conda-forge is a GitHub organization containing repos of conda recipes...

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
see https://pymolwiki.org/index.php/Advanced_Coloring

also: https://bioinformatics.stackexchange.com/questions/2859/how-to-colour-multiple-residues-in-pymol

        select toBeColored, ((i. 10-20 or i. 30-40) and c. L ) or ((i. 5-10+20-30) and c. H)
        color yellow, toBeColored
        
Handy pymol for beginners link: https://dasher.wustl.edu/bio5357/software/pymol/beginners.pdf 
        


## Viewing multiple structures in pymol

open strutcures then do:

        set grid_mode, 1     #This will separate each structure in a grid (so they don't overlap) 
        alignto    # aligns structures 








