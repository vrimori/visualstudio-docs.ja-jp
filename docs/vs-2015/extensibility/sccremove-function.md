---
title: SccRemove 関数 |Microsoft Docs
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
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b97e04c33b75dbee4fae4cd30f3de8a9aea3bd0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537911"
---
# <a name="sccremove-function"></a>SccRemove 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[SccRemove 関数](https://docs.microsoft.com/visualstudio/extensibility/sccremove-function)します。  
  
この関数は、ソース管理システムからファイルを削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]削除するファイルの完全修飾のローカル パス名の配列。  
  
 lpComment  
 [in]削除される各ファイルに適用されるコメントです。  
  
 方法は限られて  
 [in]コマンドのフラグ (未使用)。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプション。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|アンインストールが正常に完了しました。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース管理下ではありません。|  
|SCC_E_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートしません。|  
|SCC_E_ISCHECKEDOUT|ユーザーが現在チェック アウトを持つために、ファイルを削除できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。ファイルは削除されませんでした。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、ソース管理システムからファイルを削除しますが、ユーザーのローカル ハード ドライブからは削除されません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)

