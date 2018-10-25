---
title: SccAddFromScc 関数 |Microsoft Docs
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
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dcf45aa6eb5abbdb7442adf2b65c8a2eea3e9c83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870537"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ソース管理システムに既に存在するファイルの参照をでき、その後に、現在のプロジェクトの一環としてそのファイル。 たとえば、この関数は、ファイルをコピーせず、現在のプロジェクトに共通のヘッダー ファイルを取得できます。 ファイルの戻り値の配列`lplpFileNames`ユーザーが、IDE プロジェクトを追加するファイルの一覧が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpnFiles  
 [入力、出力]追加されたファイルの数をバッファーします。 (これは`NULL`によってメモリを指している場合`lplpFileNames`を解放します。 詳細については「解説」を参照します。)  
  
 lplpFileNames  
 [入力、出力]ディレクトリ パスがないすべてのファイル名へのポインターの配列。 この配列が割り当てられ、ソース管理プラグインによって解放されます。 場合`lpnFiles`= 1 と`lplpFileNames`ない`NULL`、によって示される配列の最初の名前`lplpFileNames`コピー先のフォルダーが含まれています。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ファイルが正常にあるし、プロジェクトに追加します。|  
|SCC_I_OPERATIONCANCELED|効果なしでは、操作が取り消されました。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
  
## <a name="remarks"></a>Remarks  
 IDE では、この関数を呼び出します。 ソース管理プラグインは、ローカルのコピー先フォルダーを指定することをサポートする場合に、IDE が合格`lpnFiles`= 1 とにローカル フォルダー名を渡します`lplpFileNames`します。  
  
 ときに呼び出し、`SccAddFromScc`プラグインが値を割り当て、関数を返します`lpnFiles`と`lplpFileNames`、必要に応じて、ファイル名の配列のメモリの割り当て (でポインターがこの割り当てににより置き換えられることに注意してください。 `lplpFileNames`)。 ソース管理プラグインは、ユーザーのディレクトリにまたは指定された指定のフォルダーには、すべてのファイルを配置する責任を負います。 次に、IDE は、IDE プロジェクトにファイルを追加します。  
  
 最後に、IDE を呼び出すこの関数に渡して、もう一度`NULL`の`lpnFiles`します。 これはソース管理プラグインでファイル名の配列に割り当てられたメモリを解放して特別なシグナルとして解釈されます。 `lplpFileNames``.`  
  
 `lplpFileNames` `char ***`ポインター。 ソース管理プラグインは、この API の標準的な方法で一覧を渡すためのファイル名へのポインターの配列へのポインターを配置します。  
  
> [!NOTE]
>  VSSCI API の最初のバージョンでは、ターゲットのプロジェクトを追加したファイルを示す方法は提供しませんでした。 これのセマンティクスに合わせて、`lplpFIleNames`パラメーターが出力パラメーターではなく、入力/出力パラメーターに強化されています。 1 つのファイルを指定すると、専用の場合は、値によって示される`lpnFiles`= 1、最初の要素の`lplpFileNames`ターゲット フォルダーが含まれています。 このような新しいセマンティクスを IDE の呼び出しを使用する、`SccSetOption`関数と、`nOption`パラメーターに設定`SCC_OPT_SHARESUBPROJ`します。 返すかどうか、ソース管理プラグインは、セマンティクスをサポートしていません、`SCC_E_OPTNOTSUPPORTED`します。 無効にします。 そのための使用を行って、**ソース管理から追加**機能します。 プラグインをサポートしている場合、**ソース管理から追加**機能 (`SCC_CAP_ADDFROMSCC`)、次に新しいセマンティクスをサポートし、返す必要があります`SCC_I_SHARESUBPROJOK`します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)

