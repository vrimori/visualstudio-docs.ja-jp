---
title: CreatePkgDef ユーティリティ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 312bbab46cfb7dec85e42f425b2363c2442e576b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016227"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef ユーティリティ
パラメーターとして Visual Studio 拡張機能の .dll ファイルを受け取り、作成、 *.pkgdef*付随するファイル、 *.dll*ファイル。 *.Pkgdef*ファイルには、拡張機能がインストールされている場合、システム レジストリに書き込まそれ以外の場合は、すべての情報が含まれています。  
  
> [!NOTE]
>  自動的に Visual Studio SDK に含まれるプロジェクト テンプレートのほとんど作成 *.pkgdef*ビルド プロセスの一環としてファイル。 このドキュメントはパッケージを手動で作成または使用する既存のパッケージを変換する必要がある場合、 *.pkgdef*展開します。  
  
## <a name="syntax"></a>構文  
  
```  
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>  
```  
  
## <a name="arguments"></a>引数  
 **/out=&lt;FileName&gt;**  
 必須。 名前を設定、 *.pkgdef*の出力ファイルを&lt;FileName&gt;します。  
  
 **/codebase**  
 任意。 登録を強制的に、**コードベース**ユーティリティ。  
  
 **/assembly**  
 登録を強制的に、**アセンブリ**ユーティリティ。  
  
 **&lt;AssemblyPath&gt;**  
 パス、 *.dll*ファイルを生成する、 *.pkgdef*します。  
  
## <a name="remarks"></a>Remarks  
 使用して拡張機能の配置 *.pkgdef*ファイルには、Visual Studio の以前のバージョンのレジストリの要件が置き換えられます。  
  
 *.Pkgdef*ファイルは、次の場所のいずれかでインストールする必要があります。 

- *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\* 
 
- *%vsinstalldir%\Common7\IDE\Extensions\\*
    
  インストール フォルダーがある場合 *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*、拡張機能は、Visual Studio によって認識されますは既定で無効になります。 ユーザーを使用して、拡張機能を有効にできます**拡張機能と更新**します。 
   
  インストール フォルダーがある場合 *%vsinstalldir%\Common7\IDE\Extensions\\*、拡張機能が既定で有効にします。  
  
> [!NOTE]
>  **拡張機能と更新**ツールは VSIX パッケージの一部としてインストールされていない場合、拡張機能へのアクセスに使用できません。  
  
## <a name="see-also"></a>関連項目  
 [CreateExpInstance ユーティリティ](../../extensibility/internals/createexpinstance-utility.md)