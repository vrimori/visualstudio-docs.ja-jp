---
redirect_url: shell/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files
title: "使用される文字列を置換します。Pkgdef およびです。Pkgundef ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 220e6d9bb9d360a51f9a83b5d0b4420cf64aef91
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>使用される文字列を置換します。Pkgdef およびです。Pkgundef ファイル
分離シェル アプリケーションの Visual Studio 用に定義した .pkgundef ファイルと、.pkgdef に以下の代替文字列を使用できます。  
  
## <a name="substitution-strings"></a>代替文字列  
  
|文字列型|説明|  
|------------|-----------------|  
|$=*レジストリ エントリ*$|値、*のレジストリ エントリ*エントリです。 レジストリ エントリの文字列は円記号で終わっている場合 (\\)、レジストリ サブキーの既定値が使用されます。 たとえば、$ の文字列置換 = HKEY_CURRENT_USER\Environment\TEMP$ を現在のユーザーの一時フォルダを展開します。|  
|$AppName $|AppEnv.dll エントリ ポイントに渡されるアプリケーションの修飾名。 修飾名は、アプリケーション名、アンダー スコア、およびプロジェクト .pkgdef ファイルで ThisVersionDTECLSID 設定の値としても記録されますが、アプリケーション オートメーション オブジェクトのクラス id (CLSID) で構成されます。|  
|$AppDataLocalFolder|このアプリケーションの %localappdata% 下のサブフォルダーです。|  
|$BaseInstallDir $|Visual Studio がインストールされている場所の完全パス。|  
|$CommonFiles $|%Commonprogramfiles% 環境変数の値。|  
|$MyDocuments $|現在のユーザーの [マイ ドキュメント] フォルダーの完全パス。|  
|$PackageFolder $|アプリケーションのパッケージのアセンブリ ファイルを格納するディレクトリの完全パス。|  
|$ProgramFiles $|%Programfiles% 環境変数の値。|  
|$RootFolder $|アプリケーションのルート ディレクトリの完全パス。|  
|$RootKey $|アプリケーションのルート レジストリ キー。 既定では、ルートが、ように\\*CompanyName*\\*ProjectName*\\*VersionNumber* (場合アプリケーションが実行されている、_Config はこのキーに追加されます)。 RegistryRoot 値で設定されている、 *SolutionName*.pkgdef ファイル。<br /><br /> アプリケーションのサブキーの下のレジストリ値を取得する $RootKey$ 文字列を使用できます。 たとえば、文字列"$= $RootKey$ \AppIcon$"は、アプリケーション ルートのサブキーの下の入ったエントリの値を返します。<br /><br /> パーサーが順番に .pkgdef ファイルを処理し、エントリが以前に定義されている場合にのみアプリケーションのサブキーの下のレジストリ エントリにアクセスできます。|  
|$ShellFolder $|Visual Studio がインストールされている場所の完全パス。|  
|$System $|Windows \system32 フォルダーです。|  
|$WINDIR $|Windows フォルダーです。|  
  
 パーサーが置換文字列を認識しない文字列の部分の置換は実行されませんし、レジストリ エントリ、または、環境変数の値を判断できない場合。