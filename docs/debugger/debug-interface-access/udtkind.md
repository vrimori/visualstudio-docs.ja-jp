---
title: "UdtKind |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ba00f8e257e1ada0903e17b231f668a4eb30052a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="udtkind"></a>UdtKind
さまざまなユーザー定義型 (UDT) をについて説明します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## <a name="elements"></a>Elements  
 UdtStruct  
 UDT は、構造です。  
  
 UdtClass  
 UDT は、クラスです。  
  
 UdtUnion  
 UDT は、共用体です。  
  
 UdtInterface  
 UDT は、インターフェイスです。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値が返された、 [idiasymbol::get_udtkind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)メソッドです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>参照  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)