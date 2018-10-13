---
title: SccRename 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ef59da920e8011e5b2a23e14dcd58cdc07365d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232213"
---
# <a name="sccrename-function"></a>SccRename 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ソース管理システムでファイルを変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpFileName  
 [in]名前が変更されるファイルの完全修飾ファイル名。  
  
 lpNewName  
 [in]完全修飾の新しい名前。 ディレクトリ パスが異なる場合は、ファイルが 1 つのサブディレクトリからに移動別です。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|名前変更操作が正常に完了しました。|  
|SCC_E_PROJNOTOPEN|プロジェクトでは、ソース管理下にある開いていません。|  
|SCC_E_FILENOTCONTROLLED|ファイルはソース管理されません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。|  
|SCC_E_NOTAUTHORIZED|ユーザーは、この操作を実行する権限がありません。|  
|SCC_E_COULDNOTCREATEPROJECT|名前の変更プロセスの一部として、プロジェクトを作成できませんでした。|  
|SCC_E_OPNOTPERFORMED|操作は実行されませんでした。|  
|SCC_E_NONSPECIFICERROR|指定されていないか、一般的なエラーが発生しました。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、ファイルの名前を変更または移動する、1 つの場所から別に、ソース管理システムで使用できます。 ソース管理プラグインは、ディスク上のファイルへのアクセスを試みませんする必要があります。 ローカル ファイルの名前を変更する IDE の役目です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)

