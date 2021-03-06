# ViSenze-Fashion-Attribute-Extraction
This python script converts an <ins><a href="https://www.dropbox.com/s/qm7h8fwujnpq15t/example_input.csv?dl=1" download="example_input.csv">input fashion attribute file</ins></a> into a <ins><a href="https://www.dropbox.com/s/6s0bbq2618p1flf/fashion_attribute_example_output.csv?dl=1" download="fashion_attribute_example_output.csv">cleaned csv file</ins></a>. The <i>input fashion attribute file</i> is generated from ViSenze dashboard and contains JSON strings such as the following: 
```bash
[{"objects":[{"tags":[{"tag":"category:sport_shoes","score":0.9857027530670166},{"tag":"product_color:multi","score":0.9736108183860779},{"tag":"product_pattern:animal_print","score":0.9375014901161194},{"tag":"shoe_closure:lace","score":0.8751133680343628}],"box":[13,138,446,317]}],"debug_objects":[],"tag_group":"fashion_attributes"},{"objects":[{"tags":[{"tag":"no_text","score":0.9907019138336182}],"box":[]}],"debug_objects":[],"tag_group":"image_text"},{"objects":[{"tags":[{"tag":"costume","score":0.8016501665115356}],"box":[13,138,446,317]}],"debug_objects":[],"tag_group":"fashion_occasion"},{"objects":[{"tags":[{"tag":"no_model","score":0.999996542930603}],"box":[]}],"debug_objects":[],"tag_group":"image_human"},{"objects":[{"tags":[{"tag":"no_collage","score":0.991800844669342}],"box":[]}],"debug_objects":[],"tag_group":"image_collage"},{"objects":[{"tags":[{"tag":"streetstyle","score":0.9581801891326904}],"box":[13,138,446,317]}],"debug_objects":[],"tag_group":"fashion_style"},{"objects":[{"tags":[{"tag":"multi","score":0.7209011316299438}],"box":[]}],"debug_objects":[],"tag_group":"product_color"},{"objects":[{"tags":[{"tag":"no_mosaic","score":0.9951471090316772}],"box":[]}],"debug_objects":[],"tag_group":"image_mosaic"},{"objects":[{"tags":[{"tag":"big_graphic","score":0.6292022466659546}],"box":[]}],"debug_objects":[],"tag_group":"product_pattern"},{"objects":[{"tags":[{"tag":"no_detail","score":0.9998843669891357}],"box":[]}],"debug_objects":[],"tag_group":"image_detail"},{"objects":[],"debug_objects":[],"tag_group":"gender_detect_kid"}]
```
With <i>Fashion_attribute_extraction.py</i>, we are able to:
1. Read the input fashion attribute file
2. Extract fashion attributes as column headers and fashion details as cell contents
3. Combine the input fashion attribute file with fashion details and output the master file in CSV format 

Steps to follow before executing the script
1. Prepare product catalogue files in CSV format, including im_name and im_url (mandatory). A sample is <ins><a href="https://www.dropbox.com/s/92a4o6ax8pbur1i/product_catalogue_template.csv?dl=1" download="product_catalogue_template.csv">HERE.</ins></a> The details can be found: http://developers.visenze.com/setup/#Upload-your-datafeed

2. Upload product catalogue files on ViSenze's dashboard (Your Images -> Upload). Please remember to check Yes:

<img src="https://storage.googleapis.com/visenze-test-890215/Upload.JPG" alt="Tag uploaded product catalogue files" class="center">


3. Install Python library
```bash

$ pip3 install pandas
$ pip3 install argparse

```

Running <i>Fashion_attribute_extraction.py</i>
```bash

$ python3 ~/dir/Fashion_attribute_extraction.py -i ~/dir/your_input_fashion_attribute_filename -o ~/dir/your_output_fashion_attribute_filename

```

Integrating your datafeed with fashion attribute tagging

Data index API
```bash
$ python3 ~/dir/Visenze_insert_API.py -i ~/dir/your_output_fashion_attribute_filename -u your_Visenze_dashboard_admin_Access_Key -p your_Visenze_dashboard_admin_Secret_Key    
```
FTP_upload
```bash
$ bash ~/dir/datafeed_ftp_sample.sh --upload ~/dir/your_upload_folder_name --backup ~/dir/your_backup_folder_name --ftp ~/dir/your_ftp_folder_name --username XXX --password XXX --ftp_address XXX 
```

