---
title: "MemoryTypeEnum | Microsoft Docs"
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
  - "MemoryTypeEnum 列挙型"
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# MemoryTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

メモリ アクセスの種類を指定します。  
  
## 構文  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### パラメーター  
 `MemTypeCode`  
 がメモリしか。  
  
 `MemTypeData`  
 Access データまたはスタックにメモリ。  
  
 `MemTypeStack`  
 スタックにメモリのアクセスのみ。  
  
 `MemTypeAny`  
 ようなメモリにアクセスします。  
  
## 解説  
 この列挙体の値はメモリ内の別の型へのアクセスの制限に [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) のメソッドに渡されます。  
  
## 必要条件  
 ヘッダー : cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)