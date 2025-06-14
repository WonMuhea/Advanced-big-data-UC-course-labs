{\rtf1\ansi\ansicpg1252\cocoartf2822
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;\f1\fnil\fcharset0 HelveticaNeue;}
{\colortbl;\red255\green255\blue255;\red29\green29\blue29;\red255\green255\blue255;\red0\green0\blue0;
}
{\*\expandedcolortbl;;\cssrgb\c14902\c14902\c14902;\cssrgb\c100000\c100000\c100000;\cssrgb\c0\c0\c0\c84706;
}
\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 This lab focuses on classification of wine data obtained from Sklearn Library using KNN and RNN supervised learning algorithms.\
In generate for the given dataset, we run KNN for K values 
\f1\fs28 \cf2 \cb3 \expnd0\expndtw0\kerning0
 1, 5, 11, 15, and 21 
\f0\fs24 \cf0 \cb1 \kerning1\expnd0\expndtw0 and RNN for radius values 
\f1\fs28 \cf4 \cb3 \expnd0\expndtw0\kerning0
350, 400, 450, 500, 550, and 600.\'a0
\f0\fs24 \cf0 \cb1 \kerning1\expnd0\expndtw0 \
Key Insights:  \
\
 KNN outperformed RNN.\
  KNN accuracy starts from 77% and grows as K value grows showing more accuracy.\
  RNN is found to be sensitive to radius values as increase in radius results in accuracy variability.\
\
Challenges:\
   When calculating the metrics values, division by zero was causing issues and it was resolved by further reading, }