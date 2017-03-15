---
title: "CV_call_e | Microsoft Docs"
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
helpviewer_keywords: 
  - "CV_call_e 列挙型"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

関数の呼び出し規約を指定します。  
  
> [!NOTE]
>  共通の列挙値をここに記載されています。  完全な列挙体は cvconst.h のヘッダー ファイルで使用できます。  
  
## 構文  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## Elements  
 CV\_CALL\_NEAR\_C  
 近い右から左にはを使用して関数呼び出し規約を指定します。  呼び出し元の関数がスタックを消去します。  
  
 CV\_CALL\_NEAR\_FAST  
 登録の近くに左から右にはを使用して関数呼び出し規約を指定します。  呼び出された関数がスタックを消去するためにパラメーターのバイト単位の合計を使用します。  
  
 CV\_CALL\_NEAR\_STD  
 標準近い呼び出し \(右から左\) ではを使用して関数呼び出し規約を指定します。  
  
 CV\_CALL\_NEAR\_SYS  
 \[システム コールを使用して関数呼び出し規約を指定します。  
  
 CV\_CALL\_THISCALL  
 `this` の呼び出し \(レジスタで渡された `this` のポインター\) を使用して関数呼び出し規約を指定します。  
  
 CV\_CALL\_CLRCALL  
 共通言語ランタイム \(マネージ コードの呼び出し規約\) \(CLR\) までに使用される関数呼び出し規約を指定します。  
  
## 解説  
 この列挙体の値は [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) メソッドの呼び出しによって返されます。  
  
## 必要条件  
 ヘッダー : cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)