---
title: SccHistory 関数 |Microsoft Docs
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
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dd296d84d9d5bed9394a565f9692dd9a8aac069
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911955"
---
# <a name="scchistory-function"></a>SccHistory 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、指定されたファイルの履歴を表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvContext`  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 `hWnd`  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 `nFiles`  
 [in]指定されたファイルの数、`lpFileName`配列。  
  
 `lpFileName`  
 [in]ファイルの完全修飾名の配列。  
  
 `fOptions`  
 [in]コマンドのフラグ (現在使用しません)。  
  
 `pvOptions`  
 [in]ソース管理プラグインに固有のオプション。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|バージョン履歴が正常に取得します。|  
|SCC_I_RELOADFILE|ソース管理システムが実際にディスク上のファイルを変更 (たとえば、その古いバージョンの取得)、によって、履歴をフェッチ中に、IDE は、このファイルを再読み込みする必要があります。|  
|SCC_E_FILENOTCONTROLLED|ファイルはソース管理されません。|  
|SCC_E_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートしません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_PROJNOTOPEN|プロジェクトが開かれました。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。 ファイル履歴を取得できませんでした。|  
  
## <a name="remarks"></a>Remarks  
 ソース管理プラグインは、各ファイルの履歴を表示する独自のダイアログ ボックスを表示できますを使用して`hWnd`として親ウィンドウ。 または、省略可能なテキストがコールバックを出力に指定された関数、 [SccOpenProject](../extensibility/sccopenproject-function.md)サポートされている場合は、使用できます。  
  
 特定の状況ではこの呼び出しの実行中に検査するファイルが変更可能性がありますに注意してください。 たとえば、[!INCLUDE[vsvss](../includes/vsvss-md.md)]履歴コマンドは、ファイルの古いバージョンを取得する機会をユーザーに提供します。 このような場合は、ソース管理プラグインを返します。`SCC_I_RELOAD`にファイルを再読み込みする必要があることを IDE に警告します。  
  
> [!NOTE]
>  ソース管理プラグインがファイルの配列をこの関数をサポートしない場合は、最初のファイルのファイル履歴のみを表示できます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)

