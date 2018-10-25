---
title: 使用される文字列を置換します。Pkgdef とします。Pkgundef ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f679f5c4f817002fa92475a1fba7dc38caa34984
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175293"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>使用される文字列を置換します。Pkgdef とします。Pkgundef ファイル
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

分離シェル アプリケーションの Visual Studio 用に定義した .pkgundef ファイルと、.pkgdef に以下の代替文字列を使用できます。  
  
## <a name="substitution-strings"></a>代替文字列  
  
|String|説明|  
|------------|-----------------|  
|$=*レジストリ エントリ*$|値、*のレジストリ エントリ*エントリ。 レジストリ エントリの文字列は円記号で終わっている場合 (\\)、レジストリ サブキーの既定値が使用されます。 たとえば、$ の文字列置換 = HKEY_CURRENT_USER\Environment\TEMP$ が現在のユーザーの一時フォルダーを展開します。|  
|$AppName $|AppEnv.dll のエントリ ポイントに渡されるアプリケーションの修飾名。 修飾名は、アプリケーション名、アンダー スコア、およびプロジェクトの .pkgdef ファイルで ThisVersionDTECLSID 設定の値としても記録されますが、アプリケーション オートメーション オブジェクトのクラス id (CLSID) で構成されます。|  
|$AppDataLocalFolder|このアプリケーションの %localappdata% 下のサブフォルダーです。|  
|$BaseInstallDir $|Visual Studio がインストールされている場所の完全パス。|  
|$CommonFiles $|%Commonprogramfiles% 環境変数の値。|  
|$MyDocuments $|現在のユーザーのマイ ドキュメント フォルダーの完全パス。|  
|$PackageFolder $|アプリケーションのパッケージのアセンブリ ファイルを含むディレクトリの完全パス。|  
|$ProgramFiles $|%Programfiles% 環境変数の値。|  
|$RootFolder $|アプリケーションのルート ディレクトリの完全パス。|  
|$RootKey $|アプリケーションのルート レジストリ キー。 Hkey_current_user のルートは、既定で\\*CompanyName*\\*ProjectName*\\*VersionNumber* (場合アプリケーションが実行されている、_Config がこのキーに追加されます)。 RegistryRoot 値で設定されている、 *SolutionName*.pkgdef ファイル。<br /><br /> アプリケーションのサブキーの下のレジストリ値を取得する $RootKey$ の文字列を使用できます。 たとえば、文字列"$= $RootKey \AppIcon$"はアプリケーションのルートのサブキーの下の AppIcon エントリの値を返します。<br /><br /> パーサーが順番に .pkgdef ファイルを処理し、エントリは既に定義されている場合にのみアプリケーション サブキーのレジストリ エントリにアクセスできます。|  
|$ShellFolder $|Visual Studio がインストールされている場所の完全パス。|  
|$System $|Windows \system32 フォルダーです。|  
|$WINDIR $|Windows のフォルダーです。|  
  
 パーサーが置換文字列を認識していないでその部分文字列の置換は実行されませんし、レジストリ エントリまたは環境変数の値を判断できない場合。

