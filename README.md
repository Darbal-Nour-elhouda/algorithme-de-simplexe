# algorithme-de-simplexe


```c++
num_rows=input("Entrez le nombre de lignes : "); 
%le nombre de contraintes= nombre de ligne 
num_cols=input("Entrez le nombre de colones : "); 
%le nombre de variables= nombre de colonne 
% %  ******************************************** 
%inserer la matrice A
A=input("Veuillez Entrer la matrice A: "); 

 %inserer le vecteur B (vertical)
B=input("Veuillez Entrer le vecteur B: "); 

 %inserer le vecteur C (vertical)
C=input("Veuillez entrez C: ");

I=eye(num_rows);
cb=zeros(num_rows,1);
cn=C;
a=[A,I];
Base = I;
sol=true;
while(sol)
    Bbar=inv(Base)*B;
    pi=transpose*(transpose(cb)*inv(Base));
    cnbar=transpose(cn)-transpose(pi)*A;
    contains_negative=(cnbar<0);
    if contains_negative==false
        fprintf('solution');
        break;
    end
    [minc,index]=min(cnbar);
    vectore=A(:,index);
    asbar=inv(Base)*vectore;
    contains_negativeasbar=(asbar<=0);
    if contains_negativeasbar==true
        fprintf('problème non borné');
        break;
    end
    rrows=size(find(asbar>0),1);
    r=zeros(rrows,1);
    p=1;
    for s=1:num_rows
        if asbar(s,1)>0
            r(p,1)=Bbar(s,1)/asbar(s,1);
            p=p+1;
        end
    end
    [minr,indexind]=min(r);
    er=zeros(num_rows,1);
    er(indexind,1)=1;
    ar=Base*er;
    [m,ib]=ismember(ar.',Base.','rows');
    Base(:,ib)=vectore;
    A(:,index)=ar;
    a=cb(ib,1);
    b=cn(index,1);
    cb(ib,1)=b;
    cn(index,1)=a;
end

  ```


I m -[DARBAL nour-elhouda](https://github.com/teamkhaoulanour)

Encadré par : [Mme Majda ](https://)


<p align="right">(<a href="#top">back to top</a>)</p>

