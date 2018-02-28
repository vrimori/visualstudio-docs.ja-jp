---
title: "SccProperties 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: efaa2877743fcf69a61a79633108d203442489e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccproperties-function"></a>SccProperties 関数
この関数は、ファイルまたはプロジェクトのソース コントロールのプロパティを表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpFileName  
 [in]ファイルまたはプロジェクトの完全修飾パス名。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|プロパティが正常に表示されます。|  
|SCC_I_RELOADFILE|バージョン コントロール システムが、IDE は、このファイルを再読み込みする必要がありますので、ファイルのプロパティを変更します。|  
|SCC_E_PROJNOTOPEN|ソース管理で、指定されたプロジェクトが開かれていません。|  
|SCC_E_NOTAUTHORIZED|ユーザーは、このファイルまたはプロジェクトのプロパティを表示する権限がありません。|  
|SCC_E_FILENOTCONTROLLED|指定したファイルまたはプロジェクトはソース管理されません。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明または一般的なエラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 ソース管理プラグインでは、独自のダイアログ ボックスで、プロパティが表示されます。  
  
 プロパティは、ソース管理プラグインで定義されており、プラグインをプラグインと異なる可能性があります。 かどうかにより、プラグイン ファイルのソース コントロールのプロパティを変更するユーザーを返します`SCC_I_RELOAD`をこのファイルまたはプロジェクトが再読み込みする必要がある IDE に通知します。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)