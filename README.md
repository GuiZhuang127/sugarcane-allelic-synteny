## Usage

Show help information:

```bash
Rscript make_synteny_vis.r -h
```

Basic usage:

```bash
Rscript make_synteny_vis.r \
  --info example/info.tsv \
  --out results/example_synteny
```

Example with highlighted genes and BED intervals:

```bash
Rscript make_synteny_vis.r \
  --info example/info.combinedSUS_SruZGSES \
  --highlight example/colorsbSUS \
  --bed example/peaks1.bed \
  --bed_alpha 0.5 \
  --out results/sbmultiGH9LD_mono \
  --snp FALSE
```

### Options

| Option         | Description                                                             | Default  |
| -------------- | ----------------------------------------------------------------------- | -------- |
| `--info`       | Genomic information file used to define the regions and input genomes.  | Required |
| `--upstream`   | Upstream extension length.                                              | `0`      |
| `--downstream` | Downstream extension length.                                            | `0`      |
| `--zoomin`     | Zoom-in parameter for visualization.                                    | `0`      |
| `--highlight`  | File containing genes to be highlighted.                                | `FALSE`  |
| `--bed`        | BED-like file containing intervals to be displayed on the synteny plot. | `FALSE`  |
| `--bed_alpha`  | Transparency of BED interval tracks.                                    | `0.5`    |
| `--out`        | Output file prefix.                                                     | Required |
| `--tmp`        | Temporary command file.                                                 | `tmp`    |
| `--width`      | Output figure width.                                                    | `8`      |
| `--height`     | Output figure height.                                                   | `4`      |
| `--snp`        | Whether SNPs/indels should be displayed.                                | `TRUE`   |
| `--run`        | Whether to run sequence extraction and MUMmer alignment.                | `TRUE`   |

### Input file format

The `--info` file should be a tab-delimited table with a header. It should contain the genomic regions, sample prefixes, genome FASTA files, GFF annotation files and strand information used for synteny visualization.

The `--bed` file should be a tab-delimited file with at least four columns:

```text
Prefix    Chr    Start    End
```

Optional columns can be used to provide labels, colors and track information:

```text
Prefix    Chr    Start    End    Label    Color    Track
```

### Output

The script generates a PDF file named:

```text
<out>.alignment.pdf
```
