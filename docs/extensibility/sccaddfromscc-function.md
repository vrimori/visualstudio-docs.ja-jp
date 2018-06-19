---
title: SccAddFromScc 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce2d9d179fd46bcc63340c911437486e1a459195
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139953"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 関数
この関数は、既にソース管理システムにあるファイルを参照することができ、後で、現在のプロジェクトの場合は、これらのファイル部分を作成します。 たとえば、この関数は、ファイルをコピーすることがなく、現在のプロジェクトに共通のヘッダー ファイルを取得できます。 ファイルの戻り値の配列`lplpFileNames`ユーザーが IDE のプロジェクトに追加するファイルの一覧が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpnFiles  
 [入力、出力].追加されるファイルの数をバッファーします。 (これは`NULL`メモリを指す場合`lplpFileNames`が解放されます。 詳細については「解説」を参照します。)  
  
 lplpFileNames  
 [入力、出力].ディレクトリ パスがないすべてのファイル名へのポインターの配列。 この配列が割り当てられているされ、ソース管理プラグインによって解放されます。 場合`lpnFiles`= 1 と`lplpFileNames`は`NULL`、配列の最初の名前を指す`lplpFileNames`先のフォルダーが含まれています。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ファイルが正常に配置し、プロジェクトに追加されます。|  
|SCC_I_OPERATIONCANCELED|効果なしで操作が取り消されました。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトは、再読み込みする必要があります。|  
  
## <a name="remarks"></a>コメント  
 IDE では、この関数を呼び出します。 ソース管理プラグインは、ローカルのコピー先フォルダーの指定をサポートする場合、IDE が渡されます`lpnFiles`= 1」およびにローカル フォルダー名を渡します`lplpFileNames`です。  
  
 ときにへの呼び出し、`SccAddFromScc`関数から返されたプラグインが割り当てられている値を`lpnFiles`と`lplpFileNames`、必要に応じて、ファイル名の配列のメモリの割り当て (内のポインターがこの割り当てに置き換えられます`lplpFileNames`)。 ソース管理プラグインは、ユーザーのディレクトリにまたは指定された指定のフォルダーには、すべてのファイルを配置することをします。 IDE では、IDE のプロジェクトに、ファイルが追加されます。  
  
 最後に、IDE この関数に渡して、もう一度`NULL`の`lpnFiles`します。 これは、ソース管理でファイル名の配列に割り当てられたメモリを解放するプラグインによって特殊なシグナルとして解釈されます。 `lplpFileNames``.`  
  
 `lplpFileNames` `char ***`ポインター。 ソース管理プラグインは、この API の標準の方法で一覧を渡すためのファイル名へのポインターの配列へのポインターを配置します。  
  
> [!NOTE]
>  VSSCI API の最初のバージョンは、追加されたファイルの対象となるプロジェクトを指定する手段を提供しませんでした。 これのセマンティクスに合わせて、`lplpFIleNames`パラメーターが出力パラメーターではなく、入力/出力パラメーターに強化されました。 1 つのファイルを指定すると、専用の場合は、値によって示される`lpnFiles`= 1 の場合は、最初の要素の`lplpFileNames`ターゲット フォルダーが含まれています。 これらの新しいセマンティクスを IDE の呼び出しを使用する、`SccSetOption`で機能、`nOption`パラメーターに設定`SCC_OPT_SHARESUBPROJ`です。 返すかどうかでも、ソース管理プラグインでは、セマンティクスはサポートされません、`SCC_E_OPTNOTSUPPORTED`です。 使用は無効を行って、 **ソース管理から追加**機能します。 場合、プラグインがサポート、 **ソース管理から追加**機能 (`SCC_CAP_ADDFROMSCC`) からには新しいセマンティクスをサポートする必要があります戻り`SCC_I_SHARESUBPROJOK`です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)