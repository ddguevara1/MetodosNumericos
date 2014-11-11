MetodosNumericos
================
/*
PrimerParcial

%Polinomio
clc;
clear;
disp('Programa del Polinomio');
%Pide el grado del polinomio
grado=input('Ingrese el grado del polinomio: ');
while(1);
    if grado < 0;
        grado = input('El grado de polinomio no puede ser negativo, ingrese de nuevo: ');
    else;
        break;
    end
end
for i=1:grado+1;
    coef = strcat('Ingrese los coeficientes de x^',num2str(i-1),': ');  
    polinomio(i)= input(coef);
end
s ='';
for i = grado +1:-1:1;
    if polinomio(i) == 0;
        s = strcat(s);    
    elseif polinomio(i) < 0;
        if i==1;
            s = strcat(s,num2str(polinomio(i)));
        else;
            s = strcat(s,num2str(polinomio(i)),'*x^',num2str(i-1));
        end
    else;
        if i==1;
            s = strcat(s,'+',num2str(polinomio(i)));
        else
             s = strcat(s,'+',num2str(polinomio(i)),'*x^',num2str(i-1));
        end
    end
end
disp('<--POLINOMIO INGRESADO-->');
disp(s);
coory=[];
coorx=[];
ecuacion=s;
%Introducimos los límites de la gráfica
while (1),
    ini=input('Introduzca el valor inicial:  ');
    fin=input('Introduzca el valor final:  ');
    %Comprobamos que ini>=fin
    if ini>fin
       disp('El valor iniclal no puede ser mayor que el valor final.')
    elseif ini<=fin,
       break;
    end;
end;
while (1),
   h=input('Introduzca el incremento:  ');
   if h>0 && (abs(ini)+abs(fin))>h,
      break;
   end;
end;
%Calculamos la y para cada valor de x
k = 1;
for j = ini:h:fin;
    a = 0;
    coorx(k) = j;
    for i = 1:length(polinomio);
        if i == 1;
            a = polinomio(i);
        else
            a = a + polinomio(i)*(j)^(i-1) ;
        end
          
    end
    coory(k) = a;
    k = k+1;
end


%Mostramos la tabla de valores
fprintf(' x \t \t f(x) \n');
fprintf('____________________________\n')
for i = 1:length(coorx);
    fprintf('%f \t %f\n',coorx(i),coory(i));
end

%Elegimos el Metodo para encontrar las Raices
letra='';
letra=input('Ingrese el Metodo para encontrar la Raices: Bisección(B) o Newton(N): ','s');
switch(letra)
   case 'B' 
      %Error Permitido
error = input('Ingrese el error permitido: ');
while(1);
    if error < 0;
        error = input('Ingrese el error permitido (Debe ser positivo): ');
    else
        break;
    end
end
fprintf('El error a usar es de %f \n',error);
disp('<<Buscando los puntos donde se encuentra la raiz>>');
raices = 0;
for i=1:length(coorx);
    if i < length(coorx);
        if coory(i) == 0;
            fprintf('Raiz encontrada en x = %f \n',coorx(i));
            raices = raices +1;
        elseif coory(i)*coory(i+1) < 0;
            a = coorx(i);
            c = coorx(i+1);
            Fa = coory(i);
            Fc = coory(i+1);
            b = (a + c)/2;
            Fb = 0;
            for i = 1:length(polinomio);
                if i == 1;
                    Fb = polinomio(i);
                else
                    Fb = Fb + polinomio(i)*(b)^(i-1) ;
                end
            end
            cont=0;
            while abs(Fb) >= error ;
                b = (a+c)/2;
                cont=cont+1;
                for i = 1:length(polinomio);
                    if i == 1;
                        Fb = polinomio(i);
                    else
                        Fb = Fb + polinomio(i)*(b)^(i-1) ;
                    end
                end
                if Fa*Fb <= 0;
                    c=b;
                    Fc=Fb;
                else
                    a=b;
                    Fa=Fb;
                end
                x = b;
            end
            fprintf('Raiz encontrada en x = %f Numero de veces:%d \n',x,cont);
            raices = raices + 1;
        end        
    end
end
fprintf('Numero de Raices halladas %d\n',raices);

polinomioderivado=[];
   case 'N' 
       
        for i =2 : length(polinomio);
        polinomioderivado (i-1) = (i-1)*polinomio(i);
       end
    stringderiva=[];
    for i = length(polinomioderivado):-1:1;
        if polinomioderivado(i) == 0;
            stringderiva = strcat(stringderiva);    
        elseif polinomioderivado(i) < 0;
            if i==1;
                stringderiva = strcat(stringderiva,num2str(polinomioderivado(i)));
            else;
                stringderiva = strcat(stringderiva,num2str(polinomioderivado(i)),'*x^',num2str(i-1));
            end
        else;
            if i==1;
                stringderiva = strcat(stringderiva,'+',num2str(polinomioderivado(i)));
            else
                stringderiva = strcat(stringderiva,'+',num2str(polinomioderivado(i)),'*x^',num2str(i-1));
            end
        end
    end
    disp('<--Polinomio Derivado-->');
    %Muestro el Polinomio Derivado
    disp(stringderiva);
    
   otherwise
     fprintf('la opción es incorrecta ingrese nuevamente:' );
end

*/
