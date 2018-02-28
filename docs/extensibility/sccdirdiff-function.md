---
title: "SccDirDiff 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c1f6f990bb33ddbc1d7591fa3ab9837f472f8418
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccdirdiff-function"></a>SccDirDiff 関数
この関数は、クライアントのディスク上の現在のローカル ディレクトリとソース管理下にある対応するプロジェクトの違いを表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpDirName  
 [in]視覚的な違いを表示する対象のローカル ディレクトリへの完全修飾パス。  
  
 dwFlags  
 [in]コマンドのフラグ (「解説」を参照してくださいセクション)。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプションです。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ディスク上のディレクトリでは、ソース コード管理で、プロジェクトと同じです。|  
|SCC_I_FILESDIFFER|ディスク上のディレクトリは、ソース コード管理で、プロジェクトと異なります。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトは、再読み込みする必要があります。|  
|SCC_E_FILENOTCONTROLLED|ディレクトリはソース コード管理されていません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
|SCC_E_FILENOTEXIST|ローカルのディレクトリが見つかりませんでした。|  
  
## <a name="remarks"></a>コメント  
 この関数は、ソース管理プラグインの指定したディレクトリに変更が一覧に、ユーザーに表示するよう指示するために使用されます。 プラグインは、ディスク上のユーザーのディレクトリとバージョン管理下にある対応するプロジェクトの違いを表示する、選択した形式で独自のウィンドウを開きます。  
  
 場合にすべてのディレクトリのプラグインがサポートの比較、「クイック比較」オプションがサポートされていない場合でも、ファイル名ごとにディレクトリの比較をサポートしてする必要があります。  
  
|`dwFlags`|解釈|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|大文字と小文字は (クイック diff またはビジュアルのいずれかの使用可能性があります)。|  
|SCC_DIFF_IGNORESPACE|空白文字 (クイック diff またはビジュアルのいずれかの使用可能性があります) を無視します。|  
|SCC_DIFF_QD_CONTENTS|ソース管理プラグインでサポートされている場合、ディレクトリでは、1 バイトずつをサイレント モードでを比較します。|  
|SCC_DIFF_QD_CHECKSUM|プラグインでサポートされている、サイレント モードで、チェックサムを使用してディレクトリを比較し、または、サポートされていない場合に戻って、SCC_DIFF_QD_CONTENTS です。|  
|SCC_DIFF_QD_TIME|プラグインでサポートされている、サイレント モードで、タイムスタンプを使用してディレクトリを比較し、または、サポートされていない場合はフォールバック SCC_DIFF_QD_CHECKSUM または SCC_DIFF_QD_CONTENTS にします。|  
  
> [!NOTE]
>  この関数と同じコマンド フラグを使用して、 [SccDiff](../extensibility/sccdiff-function.md)です。 ただし、ソース管理プラグインはディレクトリの"クイック diff"操作をサポートしないようにできます。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)