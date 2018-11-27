---
title: SccDirDiff 関数 |Microsoft Docs
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
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d2c45773a9d45c69cfed4f773bc5cdfcfa1c305
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791190"
---
# <a name="sccdirdiff-function"></a>SccDirDiff 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、クライアントのディスク上の現在のローカル ディレクトリとソース管理下にある対応するプロジェクトの違いを表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpDirName  
 [in]視覚的な違いを表示するか、ローカル ディレクトリへの完全修飾パス。  
  
 dwFlags  
 [in]コマンドのフラグ (「解説」を参照してください セクション)。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプション。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ディスク上のディレクトリでは、ソース コード管理で、プロジェクトと同じです。|  
|SCC_I_FILESDIFFER|ディスク上のディレクトリは、ソース コード管理で、プロジェクトと異なります。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
|SCC_E_FILENOTCONTROLLED|ディレクトリはソース コード管理されていません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
|SCC_E_FILENOTEXIST|ローカル ディレクトリが見つかりませんでした。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、ソース管理プラグインをユーザーに指定されたディレクトリへの変更の一覧を表示するよう指示するために使用されます。 プラグインは、ディスク上のユーザーのディレクトリとバージョン管理下にある対応するプロジェクトの違いを表示する、選択した形式で、独自のウィンドウを開きます。  
  
 すべてのディレクトリのプラグインがサポートの比較場合、"クイック diff"オプションがサポートされていない場合でも、ファイル名ごとにディレクトリの比較をサポートしてする必要があります。  
  
|`dwFlags`|解釈|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|大文字の比較が (クイック diff またはビジュアルのいずれかの使用可能性があります)。|  
|SCC_DIFF_IGNORESPACE|(クイック diff またはビジュアルのいずれかの使用可能性があります) の空白を無視します。|  
|SCC_DIFF_QD_CONTENTS|ソース管理プラグインのサポートをサイレント モードで、ディレクトリでは、1 バイトずつを比較します。|  
|SCC_DIFF_QD_CHECKSUM|プラグインでサポートされている、サイレント モードで、チェックサムを使用してディレクトリを比較します。 または、サポートされていない場合は SCC_DIFF_QD_CONTENTS に戻ります。|  
|SCC_DIFF_QD_TIME|プラグインでサポートされている、サイレント モードで、タイムスタンプを使用してディレクトリを比較します。 または、サポートされていない場合はフォールバック SCC_DIFF_QD_CHECKSUM または SCC_DIFF_QD_CONTENTS 場合。|  
  
> [!NOTE]
>  この関数と同じコマンド フラグを使用して、 [SccDiff](../extensibility/sccdiff-function.md)します。 ただし、ソース管理プラグインは、ディレクトリの"クイック diff"操作をサポートしないように選択可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)

