load ionosphere
% vom aveam matricea X continand 351 de vectori de dimensiune 34
% vom avea matricea Y continand 351 de vectori de dimensiune 1 good/bad

%realizeaza a repartizare arbitrara a observatiilor
cv=cvpartition(Y,'holdout',0.5);

lot_antrenare = X(cv.training(1),:);
etichete_antrenare = Y(cv.training(1));


lot_testare = X(cv.test(1),:);
etichete_testare=Y(cv.test(1));

%etichete_testare , etichete_antrenare vor contine 1 ,2 in loc de good/bad
for j=1:length(etichete_testare)
if(etichete_testare{j}=='g')
        etichete_testare_conv(j)=1;
elseif(etichete_testare{j}=='b')
            etichete_testare_conv(j)=2;
end
end
end


for i=1:length(etichete_antrenare)
if(etichete_antrenare{i}=='g')
        etichete_antrenare_conv(i)=1;
elseif(etichete_antrenare{i}=='b')
            etichete_antrenare_conv(i)=2;
end
end
end



%cauta cel mai apropriat vecin in lotul de antrenare pentru fiecare punct
%din lotul de testare
indecsi_nn = knnsearch(lot_antrenare,lot_testare,'k',1);
clase_prezise = etichete_antrenare_conv(indecsi_nn);

%classperf evaluaza perfomanta clasificatorului
CP=classperf(etichete_testare_conv, clase_prezise);

scor_recunoastere = CP.CorrectRate*100;
disp(scor_recunoastere);
