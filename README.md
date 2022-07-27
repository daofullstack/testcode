# testcode



    title = 'AGRI SMART - Disease Detection'

    if request.method == 'POST':
        if 'file' not in request.files:
            return redirect(request.url)
        file = request.files.get('file')
        if not file:
            return render_template('recommandation/disease.html', title=title)
        try:
            img = file.read()

            prediction = predict_image(img)

            prediction = Markup(str(disease_dic[prediction]))
            return render_template('recommandation/disease-result.html', prediction=prediction, title=title)
        except:
            pass


## e

    
<div style="
    width: 350px;
    height: 50rem;
    margin: 0px auto;
    color: black;
    border-radius: 25px;
    padding: 10px 10px;
    font-weight: bold;
  ">

  
  <form class="form-signin" method=post enctype=multipart/form-data>

    <h2 class="h4 mb-3 font-weight-normal"><b>Veuillez télécharger l'image</b></h2>
    <input type="file" name="file" class="form-control-file" id="inputfile" onchange="preview_image(event)" style="font-weight: bold;">
    <br>
    <br>
    <img id="output-image" class="rounded mx-auto d-block" />
    <button class="btn btn-lg btn-primary btn-block" type="submit" style="font-weight: bold;">Prédire</button>


  </form>
</div>

<script type="text/javascript">
  function preview_image(event) {
    var reader = new FileReader();
    reader.onload = function () {
      var output = document.getElementById('output-image')
      output.src = reader.result;
    }
    reader.readAsDataURL(event.target.files[0]);
  }
</script>



## dd



request.FILES['filename'].name


for filename, file in request.FILES.iteritems():
    name = request.FILES[filename].name
