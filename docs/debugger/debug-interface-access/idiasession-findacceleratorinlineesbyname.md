---
title: "IDiaSession::findAcceleratorInlineesByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したインライン関数の名前に対応するインライン フレームのシンボルの列挙体を返します。  
  
## 構文  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### パラメーター  
 `name`  
 \[入力\] 検索するインライン展開先の関数名。  
  
 `option`  
 \[入力\] `name`に対応するインライン フレームを検索するときに使用する名前の検索オプション。  詳細については、「[NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)」を参照してください。  
  
 `ppResult`  
 \[入力\] 結果で初期化される `IDiaEnumSymbols` のインターフェイス ポインターへのポインター。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合はエラー コードを返します。  
  
## 解説  
 この関数は、アクセラレータのスタブ関数内でのみ inlinees を検索します。  これは、ネイティブ C\+\+ の手順のレコードを無視します。  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)