---
title: SccCheckout 関数 |Microsoft Docs
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
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4cf1d8196c855612aab93404ca24072c8262e122
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548955"
---
# <a name="scccheckout-function"></a>SccCheckout 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[SccCheckout 関数](https://docs.microsoft.com/visualstudio/extensibility/scccheckout-function)します。  
  
完全修飾ファイル名の一覧を指定するには、この関数はそれらローカル ドライブに。 コメントは、チェック アウトされているすべてのファイルに適用されます。コメントの引数を指定できます、`null`文字列。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccCheckout (  
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
 [in]選択したファイルをチェック アウトの数。  
  
 lpFileNames  
 [in]チェック アウトするファイルの完全修飾パス名の配列。  
  
 lpComment  
 [in]これらのチェック アウトされている選択したファイルに適用されるコメントです。  
  
 方法は限られて  
 [in]コマンドのフラグ (を参照してください[特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md))。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプション。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|チェック アウトは成功しました。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース コード管理下ではありません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。 ファイル チェック アウトされませんでした。|  
|SCC_E_ALREADYCHECKEDOUT|ユーザーが既にファイルをチェック アウトします。|  
|SCC_E_FILEISLOCKED|新しいバージョンの作成を禁止するファイルがロックされています。|  
|SCC_E_FILEOUTEXCLUSIVE|別のユーザーには、このファイルの排他チェック アウトが行われます。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)

