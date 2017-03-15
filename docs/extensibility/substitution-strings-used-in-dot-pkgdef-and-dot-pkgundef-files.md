---
title: "使用される代替文字列。Pkgdef とします。Pkgundef ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>使用される代替文字列。Pkgdef とします。Pkgundef ファイル
Visual Studio 用に定義した .pkgundef ファイルの分離シェル アプリケーションと、.pkgdef に以下の代替文字列を使用できます。  
  
## <a name="substitution-strings"></a>代替文字列  
  
|文字列型|説明|  
|------------|-----------------|  
|$=*レジストリ エントリ*$|値、*のレジストリ エントリ*エントリです。 レジストリ エントリの文字列は円記号で終わっている場合 (\\)、レジストリ サブキーの既定値が使用されます。 たとえば、$ の文字列置換 = HKEY_CURRENT_USER\Environment\TEMP$ が現在のユーザーの一時フォルダを展開します。|  
|$AppName $|AppEnv.dll エントリ ポイントに渡されるアプリケーションの修飾名。 修飾名は、アプリケーション名、アンダー スコア、およびプロジェクト .pkgdef ファイルで ThisVersionDTECLSID 設定の値としても記録するアプリケーションのオートメーション オブジェクトのクラス id (CLSID) で構成されます。|  
|$AppDataLocalFolder|このアプリケーションの %localappdata% 下のサブフォルダーです。|  
|$BaseInstallDir $|Visual Studio がインストールされている場所の完全パス。|  
|$CommonFiles $|%Commonprogramfiles% 環境変数の値。|  
|$MyDocuments $|現在のユーザーのマイ ドキュメント フォルダーの完全パス。|  
|$PackageFolder $|アプリケーションのパッケージのアセンブリ ファイルを格納するディレクトリの完全パス。|  
|$ProgramFiles $|%Programfiles% 環境変数の値。|  
|$RootFolder $|アプリケーションのルート ディレクトリの完全パス。|  
|$RootKey $|アプリケーションのルート レジストリ キー。 既定では、ルートは、hkey_current_user で\\*CompanyName*\\*ProjectName*\\*VersionNumber* (アプリケーションを実行するときに _Config は付加このキーに)。 RegistryRoot 値で設定されている、 *SolutionName*.pkgdef ファイル。<br /><br /> アプリケーションのサブキーの下のレジストリ値を取得する $RootKey$ 文字列を使用できます。 たとえば、文字列"$= $RootKey \AppIcon$"は、アプリケーション ルートのサブキーの下の入ったエントリの値を返します。<br /><br /> パーサーが順番に .pkgdef ファイルを処理し、エントリが以前に定義されている場合にのみアプリケーション サブキーのレジストリ エントリにアクセスできます。|  
|$ShellFolder $|Visual Studio がインストールされている場所の完全パス。|  
|$System $|Windows \system32 フォルダーです。|  
|$WINDIR $|Windows フォルダーです。|  
  
 パーサーが置換文字列を認識しない文字列の部分に置換は実行されませんし、レジストリ エントリまたは環境変数の値を判断できない場合。
