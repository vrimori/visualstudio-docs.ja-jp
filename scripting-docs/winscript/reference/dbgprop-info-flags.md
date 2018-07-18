---
title: DBGPROP_INFO_FLAGS |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9821cde6c159712ff44438b74eea0f8e01247155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641052"
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
指定するために使用`DebugPropertyInfo`フィールド  
  
## <a name="syntax"></a>構文  
  
```  
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>メンバー  
 DBGPROP_INFO_NAME  
 初期化、`bstrName`フィールドです。  
  
 DBGPROP_INFO_TYPE  
 初期化、`bstrType`フィールドです。  
  
 DBGPROP_INFO_VALUE  
 初期化、`bstrValue`フィールドです。  
  
 DBGPROP_INFO_FULLNAME  
 初期化、`bstrFullName`フィールドです。  
  
 DBGPROP_INFO_ATTRIBUTES  
 初期化、`dwAttrib`フィールドです。  
  
 DBGPROP_INFO_DEBUGPROP  
 初期化、`pDebugProp`を含むフィールドを`IDebugProperty`インターフェイスです。  
  
 DBGPROP_INFO_AUTOEXPAND  
 [値] フィールドは、この種類のオブジェクトの使用可能な場合は、自動拡張値を含める必要がありますを指定します。  
  
## <a name="see-also"></a>関連項目  
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)