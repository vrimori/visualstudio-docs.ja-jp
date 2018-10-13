---
title: SccRunScc 関数 |Microsoft Docs
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
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bdeaead9d4534188b7731e9add0bde6d56ad7e7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242171"
---
# <a name="sccrunscc-function"></a>SccRunScc 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ソース コントロール管理ツールを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]選択したファイル名の配列。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ソース コントロール管理ツールが正常に呼び出されました。|  
|SCC_I_OPERATIONCANCELED|操作が取り消されました。|  
|SCC_E_INITIALIZEFAILED|ソース管理システムを初期化できませんでした。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。|  
|SCC_E_CONNECTIONFAILURE|ソース管理システムに接続できませんでした。|  
|SCC_E_FILENOTCONTROLLED|選択したファイルはソース管理下ではありません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 この関数には、外部管理ツールを介してさまざまなソース管理システムの機能にアクセスする呼び出し元ができます。 ユーザー インターフェイス、ソース管理システムがない場合は、ソース管理プラグインは、必要な管理機能を実行するインターフェイスを実装できます。  
  
 この関数は、カウントと、現在選択されているファイルのファイル名の配列で呼び出されます。 管理インターフェイス内のファイルを事前に選択するファイルの一覧を使用できる管理ツールがサポートする場合それ以外の場合、一覧を無視できます。  
  
 ユーザーが選択すると、この関数が呼び出される通常の**起動\<ソース管理サーバー >** から、**ファイル** -> **ソース管理**メニュー。 これは、**起動**メニュー オプションを常に無効になっているか、レジストリ エントリを設定しても非表示します。 参照してください[方法: ソース管理のプラグインをインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)詳細についてはします。 場合にのみ、この関数が呼び出されます[SccInitialize](../extensibility/sccinitialize-function.md)を返します、`SCC_CAP_RUNSCC`機能ビット (を参照してください[機能フラグ](../extensibility/capability-flags.md)詳細についてはこれと他の機能のビットで)。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [方法: ソース管理プラグインのインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [機能フラグ](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

