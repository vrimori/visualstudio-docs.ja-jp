---
title: "SccCheckin 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCheckin
helpviewer_keywords: SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f95377f79d02952c63b673d50569fac058a8573c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="scccheckin-function"></a>SccCheckin 関数
この関数は、ソース管理システムが表示され、変更を保存して、新しいバージョンを作成する以前のチェック アウトしたファイルをチェックインします。 この関数がカウントとにチェックインするファイルの名前の配列と呼ばれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]IDE のウィンドウで提供されるダイアログ ボックスをすべての親として使用できるプラグインの SCC へのハンドル。  
  
 nFiles  
 [in]チェックインする選択したファイルの数。  
  
 lpFileNames  
 [in]チェックインするファイルの完全修飾のローカル パス名の配列。  
  
 lpComment  
 [in]各チェックインされている選択したファイルに適用されるコメントです。 これは`NULL`とコメントに、ソース管理プラグインを入力する必要があります。  
  
 foptions の   
 [in]コマンドのフラグ、0 または`SCC_KEEP_CHECKEDOUT`です。  
  
 pvOptions  
 [in]SCC プラグインに固有のオプションです。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ファイルが正常にチェックインします。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース コード管理下ではありません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。 ファイルがチェックインされません。|  
|SCC_E_NOTCHECKEDOUT|ユーザーがいないファイルをチェック アウト、チェックインできないようにします。|  
|SCC_E_CHECKINCONFLICT|チェックインは実行されませんでした。<br /><br /> -別のユーザーが事前チェックし、`bAutoReconcile`が false であった。<br /><br /> - または -<br /><br /> -(たとえば、ファイルが場合バイナリ)、、自動マージを実行できません。|  
|SCC_E_VERIFYMERGE|ファイルは、自動マージにしましたが、ユーザーの確認保留中のチェックインされていません。|  
|SCC_E_FIXMERGE|ファイルは、自動マージにしましたが、手動で解決しなければならないマージ競合しているのためにチェックインされていません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトは、再読み込みする必要があります。|  
|SCC_E_FILENOTEXIST|ローカル ファイルが見つかりませんでした。|  
  
## <a name="remarks"></a>コメント  
 コメントは、チェックインされているすべてのファイルに適用されます。 コメントの引数を指定できます、`null`文字列、ソース管理プラグインが各ファイルのコメント文字列のユーザーを要求する場合。  
  
 `fOptions`引数がの値を指定することができます、`SCC_KEEP_CHECKEDOUT`でファイルを確認し、再度チェック アウトするユーザーの意図を示すフラグ。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)