---
title: "CreatePkgDef ユーティリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 47316f6bd47d5d528dc6e36dfe3a4bcb67e00909
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createpkgdef-utility"></a>CreatePkgDef ユーティリティ
.Dll ファイルをパラメーターとして Visual Studio 拡張機能の受け取りを .dll に付随する .pkgdef ファイルを作成します。 .Pkgdef ファイルには、拡張機能がインストールされている場合にシステム レジストリに書き込むことはそれ以外の場合、すべての情報が含まれています。  
  
> [!NOTE]
>  自動的に Visual Studio SDK に含まれているプロジェクト テンプレートのほとんどは、ビルド プロセスの一環として、.pkgdef ファイルを作成します。 このドキュメントは、対象としたパッケージを手動で作成または .pkgdef 展開を使用する既存のパッケージを変換します。  
  
## <a name="syntax"></a>構文  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>引数  
 /out =`FileName`  
 必須。 .Pkgdef 出力ファイルの名前を設定`FileName`です。  
  
 /codebase  
 任意。 コードベース ユーティリティを使用して登録を強制的に実行します。  
  
 /assembly  
 アセンブリ ユーティリティを使用して登録を強制的に実行します。  
  
 `AssemblyPath`  
 .Pkgdef を生成する .dll ファイルのパス。  
  
## <a name="remarks"></a>コメント  
 .Pkgdef ファイルを使用して拡張機能の配置には、Visual Studio の以前のバージョンのレジストリの要件が置き換えられます。  
  
 次の場所のいずれかで .pkgdef ファイルをインストールする必要があります: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ または %vsinstalldir%\Common7\IDE\Extensions\\です。 インストール フォルダーは、%localappdata%\Microsoft\Visual Studio\14.0\Extensions 場合\\、拡張機能は、Visual Studio によって認識されますは既定で無効になります。 ユーザーを使用して、拡張機能を有効にできます**拡張機能と更新プログラム**です。 インストール フォルダーは、%vsinstalldir%\Common7\IDE\Extensions 場合\\、拡張機能が既定で有効にします。  
  
> [!NOTE]
>  **拡張機能と更新プログラム**ツールは、VSIX パッケージの一部としてインストールされている場合を除き、拡張機能へのアクセスを使用することはできません。  
  
## <a name="see-also"></a>参照  
 [CreateExpInstance ユーティリティ](../../extensibility/internals/createexpinstance-utility.md)