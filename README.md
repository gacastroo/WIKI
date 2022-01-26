# WIKI
function string_a_real(s: string): real;
// Esta función es apropiada para el formato en que vienen los
// datos de longitud y latitud de los aeropuertos.
// Para otro formato de datos debería ser revisada.
//
// El parámetro s se recibe por valor, así que puede ser modificado
//
// Si en el parámetro hay números, se devolverá su valor en tipo REAL,
// positivo o negativo, en función de la existencia de un carácter '-'.
// Si no hay números se devuelve CERO.
var
	i : integer;
	error : integer;
	r : real;
	hay_numero : boolean;
	negativo : boolean;
	
begin
	hay_numero := FALSE;
	negativo := FALSE;
	for i := 1 to length(s) do begin
		case s[i] of
			'0'..'9' : hay_numero := TRUE;
			otherwise begin
				if s[i] = '-' then negativo := TRUE;
				delete(s,i,1);
			end;
		end;
	end;
	
	if hay_numero then begin
		val(s,r,error);
		r := r/1000;
		if negativo then r := -r;
		end
	else r := 0;
end;
