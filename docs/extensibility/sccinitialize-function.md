---
title: SccInitialize 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1146573f3d969ffc5cd56576ba92faa4e6ffdce0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139124"
---
# <a name="sccinitialize-function"></a>SccInitialize 関数
この関数は、ソース管理プラグインを初期化し、機能および統合開発環境 (IDE) に制限を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppvContext`  
 [in]ソース管理プラグインは、ここでその context 構造体へのポインターを配置できます。  
  
 `hWnd`  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 `lpCallerName`  
 [in]ソース管理プラグインを呼び出し元のプログラムの名前。  
  
 `lpSccName`  
 [入力、出力].ソース管理プラグインが、独自の名前を格納するバッファー (を超えないように`SCC_NAME_LEN`)。  
  
 `lpSccCaps`  
 [out]ソース管理プラグインの機能フラグを返します。  
  
 `lpAuxPathLabel`  
 [入力、出力].ソース管理プラグインが説明する文字列を格納するバッファー、`lpAuxProjPath`パラメーターによって返される、 [SccOpenProject](../extensibility/sccopenproject-function.md)と[SccGetProjPath](../extensibility/sccgetprojpath-function.md) (を超えないように`SCC_AUXLABEL_LEN`)。  
  
 `pnCheckoutCommentLen`  
 [out]チェック アウトのコメントの場合は、最大許容サイズを返します。  
  
 `pnCommentLen`  
 [out]その他のコメントの最大許容長を返します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ソース コントロールの初期化が成功しました。|  
|SCC_E_INITIALIZEFAILED|システムを初期化できませんでした。|  
|SCC_E_NOTAUTHORIZED|指定された操作を実行するユーザーが許可されていません。|  
|SCC_E_NONSPECFICERROR|不特定のエラーです。ソース管理システムは初期化されませんでした。|  
  
## <a name="remarks"></a>コメント  
 IDE は、ソース管理プラグインが初めて読み込まれるときに、この関数を呼び出します。 プラグインに、呼び出し元の名前などの特定の情報を渡すための IDE を使用できます。 IDE も返されるコメントや、プラグインの機能の許容最大長などの特定の情報です。  
  
 `ppvContext`を指す、`NULL`ポインター。 ソース管理プラグインが独自に使用するための構造体の割り当てし、にその構造体へのポインターを格納`ppvContext`です。 IDE はポインターを渡すこののどの VSSCI API 関数をグローバル ストレージに頼ることがなくコンテキスト情報を用意し、プラグインの複数のインスタンスをサポートするためのプラグインを許可します。 ときにこの構造体を解放する必要があります、 [SccUninitialize](../extensibility/sccuninitialize-function.md)と呼びます。  
  
 `lpCallerName`と`lpSccName`パラメーター名を交換するには、IDE とソース管理プラグインを有効にします。 複数のインスタンスを区別するために単にこれらの名前を使用することがありますか、実際には、メニューまたはダイアログ ボックスに表示される可能性があります。  
  
 `lpAuxPathLabel`パラメーターは、ソリューション ファイルに格納されへの呼び出しでプラグインをソース管理に渡されるを補助プロジェクト パスを識別するコメントとして使用する文字列、 [SccOpenProject](../extensibility/sccopenproject-function.md)です。 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 文字列を使用して"Sourcesafe:"です。他のソース管理プラグインをこの特定の文字列を使用しないで必要があります。  
  
 `lpSccCaps`パラメーターは、ソース管理プラグインのプラグインの機能を示すビットフラグを格納する場所です。 (機能ビットフラグの一覧については、次を参照してください。[機能フラグ](../extensibility/capability-flags.md))。 インスタンスのかどうか、プラグインは、機能の設定に呼び出し元に用意されているコールバック関数の場合、結果を書き込むプラグイン プラン ビット SCC_CAP_TEXTOUT です。 IDE にバージョン管理の結果に対するウィンドウ作成この通知はします。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [機能フラグ](../extensibility/capability-flags.md)