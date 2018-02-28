---
title: "EX_DBGPROP_INFO_FLAGS |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- EX_DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0af0de81c0253b72fe432cb3cefe11c362bc2ec4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="exdbgpropinfoflags"></a>EX_DBGPROP_INFO_FLAGS
指定するために使用`ExtendedDebugPropertyInfo`フィールドです。  
  
## <a name="syntax"></a>構文  
  
```  
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## <a name="members"></a>メンバー  
 EX_DBGPROP_INFO_ID  
 プロパティの識別子を初期化します。  
  
 EX_DBGPROP_INFO_NTYPE  
 プロパティの型を初期化します。  
  
 EX_DBGPROP_INFO_NVALUE  
 プロパティの値を初期化します。  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 初期化、`plb`フィールドです。  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 初期化、`pDebugExtProp`を含むフィールドを`IDebugExtendedProperty`インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [IDebugExtendedProperty インターフェイス](../../winscript/reference/idebugextendedproperty-interface.md)