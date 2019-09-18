

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
```


```python
page = requests.get("https://cora2017.kenes.com/program/meet-the-faculty#.W6lfoWepWpo")
soup = BeautifulSoup(page.text, 'html.parser')
```


```python
name_containers = soup.find_all('div', class_= 'speaker-info') 
```


```python
print(type(name_containers))
print(len(name_containers))
```

    <class 'bs4.element.ResultSet'>
    78



```python
speaker=name_containers[0]
speaker
```




    <div class="speaker-info">
    <span class="speaker-name">
    <strong>Howard Amital</strong>
    </span>
    <br/>
    <span class="speaker-bioabstract">Israel</span><br/>
    <span class="speaker-link-to-bio" onclick="Kenes.Speakers.SpeakerModal.OpenSpeakerModal(28); return false;">Show full Bio</span>
    </div>




```python
# Find out the name of first speaker
speaker_name=speaker.find('span',class_='speaker-name')
```


```python
speaker_name.text.strip()
```




    'Howard Amital'




```python
# Lists to store the scarped data from web page
names =[]

# Extract data from individual name container
for speaker in name_containers:
    speaker_name=speaker.find('span',class_='speaker-name')
    if speaker_name is not None:
        name = speaker_name.text.strip()
        names.append(name)       
```


```python
# Creat two variables
df = pd.DataFrame({'Speaker':names, 'Name_Modified':names})
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Speaker</th>
      <th>Name_Modified</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Howard Amital</td>
      <td>Howard Amital</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alessandro Antonelli</td>
      <td>Alessandro Antonelli</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Laurent Arnaud</td>
      <td>Laurent Arnaud</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Fabiola Atzeni</td>
      <td>Fabiola Atzeni</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Xenofon Baraliakos</td>
      <td>Xenofon Baraliakos</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Thomas Bardin</td>
      <td>Thomas Bardin</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Joanne Bargman</td>
      <td>Joanne Bargman</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Franco Bassetto</td>
      <td>Franco Bassetto</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Alberto Batticciotto</td>
      <td>Alberto Batticciotto</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Nicola Bizzaro</td>
      <td>Nicola Bizzaro</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Daniel Blockmans</td>
      <td>Daniel Blockmans</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Claudio Borghi</td>
      <td>Claudio Borghi</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Dimitrios Boumpas</td>
      <td>Dimitrios Boumpas</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Antonio Brucato</td>
      <td>Antonio Brucato</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Ian Bruce</td>
      <td>Ian Bruce</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Roberto Caporali</td>
      <td>Roberto Caporali</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Ricard Cervera</td>
      <td>Ricard Cervera</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Joab Chapman</td>
      <td>Joab Chapman</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Ernest Choy</td>
      <td>Ernest Choy</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Luca Cimino</td>
      <td>Luca Cimino</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Jan Willem Cohen Tervaert</td>
      <td>Jan Willem Cohen Tervaert</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Fabrizio Conti</td>
      <td>Fabrizio Conti</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Nathalie Costedoat Chalumeau</td>
      <td>Nathalie Costedoat Chalumeau</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Maria Cuadrado</td>
      <td>Maria Cuadrado</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Laszlo Czirjak</td>
      <td>Laszlo Czirjak</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Atul Deodhar</td>
      <td>Atul Deodhar</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Andrea Doria</td>
      <td>Andrea Doria</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Christopher Edwards</td>
      <td>Christopher Edwards</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Gianfranco Ferraccioli</td>
      <td>Gianfranco Ferraccioli</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Clodoveo Ferri</td>
      <td>Clodoveo Ferri</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>48</th>
      <td>Marco Mattucci-Cerinic</td>
      <td>Marco Mattucci-Cerinic</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Riccardo Meliconi</td>
      <td>Riccardo Meliconi</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Pierluigi Meroni</td>
      <td>Pierluigi Meroni</td>
    </tr>
    <tr>
      <th>51</th>
      <td>Pierre Miossec</td>
      <td>Pierre Miossec</td>
    </tr>
    <tr>
      <th>52</th>
      <td>Carlomaurizio Montecucco</td>
      <td>Carlomaurizio Montecucco</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Gabriella Moroni</td>
      <td>Gabriella Moroni</td>
    </tr>
    <tr>
      <th>54</th>
      <td>Yakov Naparstek</td>
      <td>Yakov Naparstek</td>
    </tr>
    <tr>
      <th>55</th>
      <td>Ignazio Olivieri</td>
      <td>Ignazio Olivieri</td>
    </tr>
    <tr>
      <th>56</th>
      <td>Pierantonio Ostuni</td>
      <td>Pierantonio Ostuni</td>
    </tr>
    <tr>
      <th>57</th>
      <td>Vittorio Pengo</td>
      <td>Vittorio Pengo</td>
    </tr>
    <tr>
      <th>58</th>
      <td>Giorgio Perino</td>
      <td>Giorgio Perino</td>
    </tr>
    <tr>
      <th>59</th>
      <td>Roberto Perricone</td>
      <td>Roberto Perricone</td>
    </tr>
    <tr>
      <th>60</th>
      <td>Niccolò Possemato</td>
      <td>Niccolò Possemato</td>
    </tr>
    <tr>
      <th>61</th>
      <td>Leonardo Punzi</td>
      <td>Leonardo Punzi</td>
    </tr>
    <tr>
      <th>62</th>
      <td>Luca Quartuccio</td>
      <td>Luca Quartuccio</td>
    </tr>
    <tr>
      <th>63</th>
      <td>Luigi Raio</td>
      <td>Luigi Raio</td>
    </tr>
    <tr>
      <th>64</th>
      <td>Roberta Ramonda</td>
      <td>Roberta Ramonda</td>
    </tr>
    <tr>
      <th>65</th>
      <td>Gabriela Reimekasten</td>
      <td>Gabriela Reimekasten</td>
    </tr>
    <tr>
      <th>66</th>
      <td>Andrea Rubbert-Roth</td>
      <td>Andrea Rubbert-Roth</td>
    </tr>
    <tr>
      <th>67</th>
      <td>Carlo Salvarani</td>
      <td>Carlo Salvarani</td>
    </tr>
    <tr>
      <th>68</th>
      <td>Piercarlo Sarzi Puttini</td>
      <td>Piercarlo Sarzi Puttini</td>
    </tr>
    <tr>
      <th>69</th>
      <td>Matthias Schneider</td>
      <td>Matthias Schneider</td>
    </tr>
    <tr>
      <th>70</th>
      <td>Yehuda Shoenfeld</td>
      <td>Yehuda Shoenfeld</td>
    </tr>
    <tr>
      <th>71</th>
      <td>Luigi Sinigaglia</td>
      <td>Luigi Sinigaglia</td>
    </tr>
    <tr>
      <th>72</th>
      <td>Zoltan Szekanecz</td>
      <td>Zoltan Szekanecz</td>
    </tr>
    <tr>
      <th>73</th>
      <td>Maria Tektonidou</td>
      <td>Maria Tektonidou</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Angela Tincani</td>
      <td>Angela Tincani</td>
    </tr>
    <tr>
      <th>75</th>
      <td>Renato Tozzoli</td>
      <td>Renato Tozzoli</td>
    </tr>
    <tr>
      <th>76</th>
      <td>Gabriele Valentini</td>
      <td>Gabriele Valentini</td>
    </tr>
    <tr>
      <th>77</th>
      <td>Guido Valesini​</td>
      <td>Guido Valesini​</td>
    </tr>
  </tbody>
</table>
<p>78 rows × 2 columns</p>
</div>




```python
# Creat a dictionary
items={
    "Fabiola Atzeni": "Nephrologist",
    "Xenofon Baraliakos": "Doctor",
    "Thomas": "Tom",
    "Daniel": "Dan"   
}
```


```python
# Replace the names in Speaker column with new ones
df.replace({"Name_Modified":items},regex=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Speaker</th>
      <th>Name_Modified</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Howard Amital</td>
      <td>Howard Amital</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alessandro Antonelli</td>
      <td>Alessandro Antonelli</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Laurent Arnaud</td>
      <td>Laurent Arnaud</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Fabiola Atzeni</td>
      <td>Nephrologist</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Xenofon Baraliakos</td>
      <td>Doctor</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Thomas Bardin</td>
      <td>Tom Bardin</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Joanne Bargman</td>
      <td>Joanne Bargman</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Franco Bassetto</td>
      <td>Franco Bassetto</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Alberto Batticciotto</td>
      <td>Alberto Batticciotto</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Nicola Bizzaro</td>
      <td>Nicola Bizzaro</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Daniel Blockmans</td>
      <td>Dan Blockmans</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Claudio Borghi</td>
      <td>Claudio Borghi</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Dimitrios Boumpas</td>
      <td>Dimitrios Boumpas</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Antonio Brucato</td>
      <td>Antonio Brucato</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Ian Bruce</td>
      <td>Ian Bruce</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Roberto Caporali</td>
      <td>Roberto Caporali</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Ricard Cervera</td>
      <td>Ricard Cervera</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Joab Chapman</td>
      <td>Joab Chapman</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Ernest Choy</td>
      <td>Ernest Choy</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Luca Cimino</td>
      <td>Luca Cimino</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Jan Willem Cohen Tervaert</td>
      <td>Jan Willem Cohen Tervaert</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Fabrizio Conti</td>
      <td>Fabrizio Conti</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Nathalie Costedoat Chalumeau</td>
      <td>Nathalie Costedoat Chalumeau</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Maria Cuadrado</td>
      <td>Maria Cuadrado</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Laszlo Czirjak</td>
      <td>Laszlo Czirjak</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Atul Deodhar</td>
      <td>Atul Deodhar</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Andrea Doria</td>
      <td>Andrea Doria</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Christopher Edwards</td>
      <td>Christopher Edwards</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Gianfranco Ferraccioli</td>
      <td>Gianfranco Ferraccioli</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Clodoveo Ferri</td>
      <td>Clodoveo Ferri</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>48</th>
      <td>Marco Mattucci-Cerinic</td>
      <td>Marco Mattucci-Cerinic</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Riccardo Meliconi</td>
      <td>Riccardo Meliconi</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Pierluigi Meroni</td>
      <td>Pierluigi Meroni</td>
    </tr>
    <tr>
      <th>51</th>
      <td>Pierre Miossec</td>
      <td>Pierre Miossec</td>
    </tr>
    <tr>
      <th>52</th>
      <td>Carlomaurizio Montecucco</td>
      <td>Carlomaurizio Montecucco</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Gabriella Moroni</td>
      <td>Gabriella Moroni</td>
    </tr>
    <tr>
      <th>54</th>
      <td>Yakov Naparstek</td>
      <td>Yakov Naparstek</td>
    </tr>
    <tr>
      <th>55</th>
      <td>Ignazio Olivieri</td>
      <td>Ignazio Olivieri</td>
    </tr>
    <tr>
      <th>56</th>
      <td>Pierantonio Ostuni</td>
      <td>Pierantonio Ostuni</td>
    </tr>
    <tr>
      <th>57</th>
      <td>Vittorio Pengo</td>
      <td>Vittorio Pengo</td>
    </tr>
    <tr>
      <th>58</th>
      <td>Giorgio Perino</td>
      <td>Giorgio Perino</td>
    </tr>
    <tr>
      <th>59</th>
      <td>Roberto Perricone</td>
      <td>Roberto Perricone</td>
    </tr>
    <tr>
      <th>60</th>
      <td>Niccolò Possemato</td>
      <td>Niccolò Possemato</td>
    </tr>
    <tr>
      <th>61</th>
      <td>Leonardo Punzi</td>
      <td>Leonardo Punzi</td>
    </tr>
    <tr>
      <th>62</th>
      <td>Luca Quartuccio</td>
      <td>Luca Quartuccio</td>
    </tr>
    <tr>
      <th>63</th>
      <td>Luigi Raio</td>
      <td>Luigi Raio</td>
    </tr>
    <tr>
      <th>64</th>
      <td>Roberta Ramonda</td>
      <td>Roberta Ramonda</td>
    </tr>
    <tr>
      <th>65</th>
      <td>Gabriela Reimekasten</td>
      <td>Gabriela Reimekasten</td>
    </tr>
    <tr>
      <th>66</th>
      <td>Andrea Rubbert-Roth</td>
      <td>Andrea Rubbert-Roth</td>
    </tr>
    <tr>
      <th>67</th>
      <td>Carlo Salvarani</td>
      <td>Carlo Salvarani</td>
    </tr>
    <tr>
      <th>68</th>
      <td>Piercarlo Sarzi Puttini</td>
      <td>Piercarlo Sarzi Puttini</td>
    </tr>
    <tr>
      <th>69</th>
      <td>Matthias Schneider</td>
      <td>Matthias Schneider</td>
    </tr>
    <tr>
      <th>70</th>
      <td>Yehuda Shoenfeld</td>
      <td>Yehuda Shoenfeld</td>
    </tr>
    <tr>
      <th>71</th>
      <td>Luigi Sinigaglia</td>
      <td>Luigi Sinigaglia</td>
    </tr>
    <tr>
      <th>72</th>
      <td>Zoltan Szekanecz</td>
      <td>Zoltan Szekanecz</td>
    </tr>
    <tr>
      <th>73</th>
      <td>Maria Tektonidou</td>
      <td>Maria Tektonidou</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Angela Tincani</td>
      <td>Angela Tincani</td>
    </tr>
    <tr>
      <th>75</th>
      <td>Renato Tozzoli</td>
      <td>Renato Tozzoli</td>
    </tr>
    <tr>
      <th>76</th>
      <td>Gabriele Valentini</td>
      <td>Gabriele Valentini</td>
    </tr>
    <tr>
      <th>77</th>
      <td>Guido Valesini​</td>
      <td>Guido Valesini​</td>
    </tr>
  </tbody>
</table>
<p>78 rows × 2 columns</p>
</div>


