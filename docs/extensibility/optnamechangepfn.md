---
title: OPTNAMECHANGEPFN |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8054094083b39a8f71ae9fe6fcb908b7af29a7a3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962770"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
呼び出しで指定されたコールバック関数は、この、 [SccSetOption](../extensibility/sccsetoption-function.md) (オプションを使用して`SCC_OPT_NAMECHANGEPFN`) によるソース管理プラグイン、IDE に名前変更を通知するために使用します。  
  
## <a name="signature"></a>署名  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 pvCallerData  
 [in]以前の呼び出しで指定されたユーザーの値、 [SccSetOption](../extensibility/sccsetoption-function.md) (オプションを使用して`SCC_OPT_USERDATA`)。  
  
 pszOldName  
 [in]ファイルの元の名前。  
  
 pszNewName  
 [in]ファイルの名前が変更されました。  
  
## <a name="return-value"></a>戻り値  
 なし。  
  
## <a name="remarks"></a>Remarks  
 ソース管理操作中に、ファイルの名前を変更する場合、ソース管理プラグインはこのコールバックから名前の変更について、IDE に通知できます。  
  
 呼び出しがない IDE がこのコールバックをサポートしていない場合、 [SccSetOption](../extensibility/sccsetoption-function.md)を指定します。 かどうか、プラグインをサポートしていないこのコールバックが返されます`SCC_E_OPNOTSUPPORTED`から、 `SccSetOption` IDE がコールバックを設定しようとしたときに機能します。  
  
## <a name="see-also"></a>関連項目  
 [IDE によって実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)