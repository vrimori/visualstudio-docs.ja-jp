---
title: SccDiff 関数 |Microsoft Docs
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
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a98f35e2829bc2eb84b9604e6b16a7b4f3f9ade
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242802"
---
# <a name="sccdiff-function"></a>SccDiff 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数が表示されます (または必要に応じてだけをチェック) (ローカル ディスク) 上の現在のファイルとその最後のチェックイン バージョンの違い、ソース管理システム。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpFileName  
 [in]違いが要求されるファイル名。  
  
 方法は限られて  
 [in]コマンドのフラグ。 詳細については、「解説」を参照してください。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプション。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|作業コピーとサーバー バージョンは同じです。|  
|SCC_I_FILESDIFFERS|作業コピーは、ソース管理下のバージョンによって異なります。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
|SCC_E_FILENOTCONTROLLED|ファイルはソース管理されません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。ファイルの相違点は取得されませんでした。|  
|SCC_E_FILENOTEXIST|ローカル ファイルが見つかりませんでした。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、2 つの異なる役割を果たします。 既定では、変更の一覧をファイルが表示されます。 ソース管理プラグインは、ディスク上のユーザーのファイルとソース管理下にあるファイルの最新バージョンの違いを表示する選択がどのような形式で、独自のウィンドウを開きます。  
  
 または、IDE では、ファイルが変更されたかどうかを判断する必要がありますだけです。 たとえば、IDE では、ユーザーに通知せずに、ファイルをチェック アウトしても安全かどうかを確認する必要があります。 その場合は、IDE の渡します、`SCC_DIFF_CONTENTS`フラグ。 ソース管理プラグインはする必要があります、バイトで、ソース管理の対象ファイルに対して、ディスク上のファイルを確認し、ユーザーに何も表示せず、2 つのファイルが異なるかどうかを示す値を返します。  
  
 ソース管理プラグイン、パフォーマンスの最適化として、チェックサムまたは for by というバイト単位の比較ではなく、タイムスタンプに基づく別の方法を使用できます`SCC_DIFF_CONTENTS`: 比較のこれらのフォームが明らかに迅速になりますが、信頼性は低くなります。 すべてのソース管理システムは、これらの代替の比較メソッドをサポート可能性があり、プラグインの内容の比較にフォールバックする必要があります。 すべてソース管理プラグインをする必要があります、少なくとも、サポート内容の比較。  
  
> [!NOTE]
>  クイック違いフラグは、相互に排他的です。 フラグに合格することは、同時に 1 つ以上を渡すことはできません。 `SCC_DIFF_QUICK_DIFF`をテストするにはすべてのフラグを結合するマスクを使用できますが、決してをパラメーターとして渡す必要があります。  
  
|`fOption`|説明|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|大文字の比較が (クイックまたはビジュアルのいずれかの違いの使用可能性があります)。|  
|SCC_DIFF_IGNORESPACE|(クイックまたはビジュアルのいずれかの違いの使用可能性があります) の空白を無視します。|  
|SCC_DIFF_QD_CONTENTS|サイレント モードで、1 バイトずつファイルを比較します。|  
|SCC_DIFF_QD_CHECKSUM|サイレント モードでサポートされている場合、チェックサムを使用してファイルを比較します。 サポートされていない場合は、内容の比較にフォールバックします。|  
|SCC_DIFF_QD_TIME|サイレント モードでサポートされている場合は、そのタイムスタンプを使用してファイルを比較します。 サポートされていない場合は、内容の比較にフォールバックします。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)

