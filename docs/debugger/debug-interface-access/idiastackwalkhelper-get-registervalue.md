---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2::get_registerValue メソッド"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

レジスタの値を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### パラメーター  
 `index`  
 \[入力\] から値を取得するように指定する [CV\_HREG\_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md) の列挙体からの値の登録。  
  
 `pRetVal`  
 \[入力\] 登録の現在の値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 `pRetVal` のパラメーターのサイズにかかわらず実装は登録が保持するものだけを格納する必要があります。  たとえば8 ビット レジスタが指定した値から最小 8bit のみを保持します。  この 8 ビット値にはこのメソッドから返されたときに配置されます。  
  
## 参照  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md)