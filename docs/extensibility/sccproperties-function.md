---
title: SccProperties 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f8067464802899ce8966d63d702679d216b6377
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875977"
---
# <a name="sccproperties-function"></a>SccProperties 関数
この関数は、ファイルまたはプロジェクトのソース管理のプロパティを表示します。  
  
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
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpFileName  
 [in]ファイルまたはプロジェクトの完全修飾パス名。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|プロパティが正常に表示されます。|  
|SCC_I_RELOADFILE|IDE は、このファイルを再読み込みする必要がありますので、バージョン管理システムがファイルのプロパティを変更します。|  
|SCC_E_PROJNOTOPEN|ソース管理で、指定されたプロジェクトが開かれていません。|  
|SCC_E_NOTAUTHORIZED|ユーザーは、このファイルまたはプロジェクトのプロパティを表示する権限がありません。|  
|SCC_E_FILENOTCONTROLLED|指定したファイルまたはプロジェクト ソース管理下にない。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明または一般的なエラーが発生しました。|  
  
## <a name="remarks"></a>Remarks  
 ソース管理プラグインは、独自のダイアログ ボックスのプロパティを表示します。  
  
 プロパティはソース管理プラグインによって定義され、プラグインのプラグインに異なる場合があります。 かどうかにより、プラグイン ファイルのソース コントロールのプロパティを変更するユーザーが返されます`SCC_I_RELOAD`をこのファイルまたはプロジェクトが再読み込みする必要がある IDE の通知。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)