---
title: EX_DBGPROP_INFO_FLAGS |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- EX_DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66ff43cd51977bf0c23ca0e024a2e05b53f5022
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878090"
---
# <a name="exdbgpropinfoflags"></a>EX_DBGPROP_INFO_FLAGS
指定するために使用`ExtendedDebugPropertyInfo`フィールド。  
  
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
 初期化します、`plb`フィールド。  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 初期化します、`pDebugExtProp`フィールドを含む、`IDebugExtendedProperty`インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [IDebugExtendedProperty インターフェイス](../../winscript/reference/idebugextendedproperty-interface.md)