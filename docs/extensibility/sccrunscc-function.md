---
title: "SccRunScc 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRunScc
helpviewer_keywords: SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ad179325c4f34cd206a3c5e6b0840a69dd46037
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccrunscc-function"></a>SccRunScc 関数
この関数は、ソース管理の管理ツールを起動します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]選択したファイル名の配列。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ソース コントロール管理ツールが正常に呼び出されます。|  
|SCC_I_OPERATIONCANCELED|操作が取り消されました。|  
|SCC_E_INITIALIZEFAILED|ソース管理システムを初期化できませんでした。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。|  
|SCC_E_CONNECTIONFAILURE|ソース管理システムへの接続に失敗しました。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース管理下ではありません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 この関数には、外部管理ツールを使ってさまざまなソース管理システムの機能にアクセスする呼び出し元ができます。 ソース管理システムがユーザー インターフェイスを持たない場合、ソース管理プラグインは、必要な管理機能を実行するインターフェイスを実装できます。  
  
 この関数は、数と現在選択されているファイルのファイル名の配列を使用します。 管理インターフェイス内のファイルを事前に選択するファイルの一覧を使用できる管理ツールでサポートされる場合、それ以外の場合、一覧を無視できます。  
  
 ユーザーを選択すると、この関数は通常呼び出されます、**起動\<ソース管理サーバー >**から、**ファイル** -> **ソース管理**メニューです。 これは、**起動**メニュー オプションを常に無効になっているやレジストリ エントリを設定しても非表示にします。 参照してください[する方法: ソース管理プラグインをインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)詳細についてはします。 場合にのみ、この関数が呼び出されます[SccInitialize](../extensibility/sccinitialize-function.md)を返します、`SCC_CAP_RUNSCC`機能ビット (を参照してください[機能フラグ](../extensibility/capability-flags.md)の詳細については、これとその他の機能ビット)。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [方法: ソース管理プラグインのインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [機能フラグ](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)