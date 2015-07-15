#include <stdlib.h>
#include "IoManager.h"

void GpsMockFunction(array_int_5  aiA429FromGps)
{
	static int i=-1;
	int j;
	for (j=0;j<5;j++)
	{
		if (j==i)
		{
			aiA429FromGps[j] = 1275068423;
		}
		else
		{
			aiA429FromGps[j] = 0;
		}
	}
	i++;
}

void IrsSpeedMockFunction(array_int_5  aiA429FromIrs)
{
	static int i=-1;
	int j;
	for (j=0;j<5;j++)
	{
		if (j==i)
		{
			aiA429FromIrs[j] = 0x2F000007;
		}
		else
		{
			aiA429FromIrs[j] = 0;
		}
	}
	i++;
}

void IrsPitchMockFunction(array_int_5  aiA429FromIrs)
{
	static int i=-1;
	int j;
	for (j=0;j<5;j++)
	{
		if (j==i)
		{
			aiA429FromIrs[j] = 0x54000007;
		}
		else
		{
			aiA429FromIrs[j] = 0;
		}
	}
	i++;
}

void IrsRollMockFunction(array_int_5  aiA429FromIrs)
{
	static int i=-1;
	int j;
	for (j=0;j<5;j++)
	{
		if (j==i)
		{
			aiA429FromIrs[j] = 0x55000007;
		}
		else
		{
			aiA429FromIrs[j] = 0;
		}
	}
	i++;
}

int main( int argc, const char ** argv )
{
	int i;
	inC_IoManager IoInputsFromSensors;
	outC_IoManager IoOutput;


	/*
	IoInputsFromSensors.aiA429FromIrs[0] = 0x2F000007;
	IoInputsFromSensors.aiA429FromIrs[1] = 0x54000007;
	IoInputsFromSensors.aiA429FromIrs[2] = 0x55000007;
	IoInputsFromSensors.aiA429FromIrs[3] = 0x2F001007;
	IoInputsFromSensors.aiA429FromIrs[4] = 0x2F000007;
	*/
	/*
	IoInputsFromSensors.aiA429FromGps[0] = 1275068423;
	IoInputsFromSensors.aiA429FromGps[1] = 1275068423;
	IoInputsFromSensors.aiA429FromGps[2] = 1275068423;
	IoInputsFromSensors.aiA429FromGps[3] = 1275068423;
	IoInputsFromSensors.aiA429FromGps[4] = 1275068416; //invalid label
	*/
	IoManager_reset(&IoOutput);
	/*
	for (i=0; i<6; i++)
	{
		GpsMockFunction(IoInputsFromSensors.aiA429FromGps);			
		IoManager(&IoInputsFromSensors,&IoOutput);
	}
	*/
	for (i=0; i<6; i++)
	{
		IrsSpeedMockFunction(IoInputsFromSensors.aiA429FromIrs);			
		IoManager(&IoInputsFromSensors,&IoOutput);
	}
	for (i=0; i<6; i++)
	{
		IrsRollMockFunction(IoInputsFromSensors.aiA429FromIrs);			
		IoManager(&IoInputsFromSensors,&IoOutput);
	}
	for (i=0; i<6; i++)
	{
		IrsPitchMockFunction(IoInputsFromSensors.aiA429FromIrs);			
		IoManager(&IoInputsFromSensors,&IoOutput);
	}
	

	
}