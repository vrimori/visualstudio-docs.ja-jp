---
title: SccProperties 関数 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb8fd8172468dc1fc4d60d0f5e36ee7b4f9a588
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535338"
---
# <a name="sccproperties-function"></a>SccProperties 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[SccProperties 関数](https://docs.microsoft.com/visualstudio/extensibility/sccproperties-function)します。  
  
この関数は、ファイルまたはプロジェクトのソース管理のプロパティを表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

