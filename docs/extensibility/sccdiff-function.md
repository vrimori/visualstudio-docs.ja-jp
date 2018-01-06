---
title: "SccDiff 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDiff
helpviewer_keywords: SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 832d80c3ca49cc03c4a66b6a4cf931dd40686c82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccdiff-function"></a>SccDiff 関数
この関数が表示されます (または必要に応じてだけをチェック) (ローカル ディスク) 上の現在のファイルと、最新のチェックインされているバージョンの違い、ソース管理システムです。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpFileName  
 [in]違いが要求されるファイル名です。  
  
 foptions の   
 [in]コマンドのフラグです。 詳細については、「解説」を参照してください。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプションです。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|作業コピーとサーバー バージョンは同じです。|  
|SCC_I_FILESDIFFERS|作業コピーは、ソース管理下のバージョンによって異なります。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトは、再読み込みする必要があります。|  
|SCC_E_FILENOTCONTROLLED|ファイルはソース管理されません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。ファイルの相違点は取得されませんでした。|  
|SCC_E_FILENOTEXIST|ローカル ファイルが見つかりませんでした。|  
  
## <a name="remarks"></a>コメント  
 この関数は、次の 2 つの異なる役割を果たします。 既定では、ファイルに変更の一覧を表示します。 ソース管理プラグインは、どのような形式のディスク上のユーザーのファイルとソース管理下にあるファイルの最新バージョンの違いを表示する、選択で独自のウィンドウを開きます。  
  
 代わりに、IDE は、ファイルが変更されたかどうかを判断するだけ必要があります。 たとえば、IDE では、ユーザーに知らせることがなく、ファイルをチェック アウトしても安全かどうかを確認する必要があります。 その場合は、IDE を渡します、`SCC_DIFF_CONTENTS`フラグ。 ソース管理プラグインは、ディスク、バイト単位でソース管理の対象ファイルに対してファイルを確認し、ユーザーに何も表示せず、2 つのファイルが異なるかどうかを示す値を返す必要があります。  
  
 パフォーマンスの最適化としてソース管理プラグイン可能性がありますを使用して、チェックサムまたはによってに対して呼び出されますバイトごとの比較ではなく、タイムスタンプに基づく`SCC_DIFF_CONTENTS`: 比較のこれらのフォームは明らかに速いが信頼性が低下します。 すべてのソース管理システムは、これらの代替の比較メソッドをサポート可能性があり、プラグインの内容の比較にフォールバックする必要があります。 すべてソース管理プラグインをする必要がありますには、少なくともサポート内容を比較します。  
  
> [!NOTE]
>  クイック違いフラグは、相互に排他的です。 フラグに合格することが同時に 1 つ以上を渡すことはできません。 `SCC_DIFF_QUICK_DIFF`をテストするにはすべてのフラグを結合するマスクを使用できますが、決してをパラメーターとして渡す必要があります。  
  
|`fOption`|説明|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|大文字と小文字は (クイックまたはビジュアルのいずれかの違いの使用可能性があります)。|  
|SCC_DIFF_IGNORESPACE|空白文字 (クイックまたはビジュアルのいずれかの違いの使用可能性があります) を無視します。|  
|SCC_DIFF_QD_CONTENTS|サイレント モードでファイルを 1 バイトずつを比較します。|  
|SCC_DIFF_QD_CHECKSUM|サイレント モードでサポートされている場合、チェックサムを使用してファイルを比較します。 サポートされていない場合は、内容の比較にフォールバックします。|  
|SCC_DIFF_QD_TIME|サイレント モードでサポートされている場合は、そのタイムスタンプを使用してファイルを比較します。 サポートされていない場合は、内容の比較にフォールバックします。|  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)