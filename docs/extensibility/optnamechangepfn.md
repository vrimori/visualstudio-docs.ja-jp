---
title: OPTNAMECHANGEPFN |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: e3ecb80b1ac0b71de935da59d29a3f5c39f85bee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137246"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
これへの呼び出しで指定されたコールバック関数、 [SccSetOption](../extensibility/sccsetoption-function.md) (オプションを使用して`SCC_OPT_NAMECHANGEPFN`) によるソース管理プラグインを IDE に戻る名の変更を通信するために使用されます。  
  
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
 [in]前の呼び出しで指定されたユーザー値、 [SccSetOption](../extensibility/sccsetoption-function.md) (オプションを使用して`SCC_OPT_USERDATA`)。  
  
 pszOldName  
 [in]ファイルの元の名前。  
  
 pszNewName  
 [in]ファイルの名前が変更されました。  
  
## <a name="return-value"></a>戻り値  
 なし。  
  
## <a name="remarks"></a>コメント  
 ソース管理操作中に、ファイルの名前を変更する場合、ソース管理プラグインはこのコールバックを介して、名前の変更は、IDE に通知できます。  
  
 IDE がこのコールバックをサポートしていない場合それを呼び出さない、 [SccSetOption](../extensibility/sccsetoption-function.md)を指定します。 かどうか、プラグインによってサポートされないこのコールバックが返されます`SCC_E_OPNOTSUPPORTED`から、 `SccSetOption` IDE がコールバックを設定しようとしたときに機能します。  
  
## <a name="see-also"></a>関連項目  
 [IDE によって実装されているコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)