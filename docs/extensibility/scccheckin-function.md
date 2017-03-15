---
title: "SccCheckin 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e8bfa87246bc866a251951e4700b796d833dd63f
ms.lasthandoff: 02/22/2017

---
# <a name="scccheckin-function"></a>SccCheckin 関数
この関数は、ソース管理システムで変更を保存して、新しいバージョンを作成する以前のチェック アウトしたファイルをチェックインします。 この関数は、カウントをチェックインするファイルの名前の配列で呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
 hwnd の分離  
 [in]プラグインの SCC は、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]チェックインを選択したファイルの数。  
  
 lpFileNames  
 [in]チェックインするファイルの完全修飾パス名の配列。  
  
 lpComment  
 [in]各チェックインされている選択したファイルに適用されるコメントです。 これは、`NULL`とコメントに、ソース管理プラグインを入力する必要があります。  
  
 される  
 [in]コマンドのフラグ、0 または`SCC_KEEP_CHECKEDOUT`です。  
  
 pvOptions  
 [in]SCC プラグインに固有のオプションです。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|ファイルがチェックインされた正常にします。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース コード管理下ではありません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。 ファイルがチェックインされません。|  
|SCC_E_NOTCHECKEDOUT|ユーザーがチェックインできないように、ファイルにはチェックされません。|  
|SCC_E_CHECKINCONFLICT|チェックインを実行できませんでした。<br /><br /> -別のユーザーがチェックイン前方および`bAutoReconcile`false であった。<br /><br /> または<br /><br /> -(たとえば、ファイルが場合バイナリ)、、自動マージを実行できません。|  
|SCC_E_VERIFYMERGE|ファイルは、自動マージにしましたが、保留中のユーザーの確認チェックされていません。|  
|SCC_E_FIXMERGE|ファイルは、自動マージにしましたが、手動で解決しなければなりませんマージの競合によってチェックインされていません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
|SCC_E_FILENOTEXIST|ローカル ファイルが見つかりませんでした。|  
  
## <a name="remarks"></a>コメント  
 コメントは、チェックインされたすべてのファイルに適用されます。 コメントの引数を指定できます、`null`文字列、ソース管理プラグインが各ファイルのコメント文字列のユーザーを要求する場合。  
  
 `fOptions`引数の値を指定することができます、`SCC_KEEP_CHECKEDOUT`ファイルをチェックインし、再度チェック アウトするユーザーの意図を示すフラグ。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)
