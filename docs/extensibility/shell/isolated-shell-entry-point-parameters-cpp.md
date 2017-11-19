---
title: "分離シェル エントリ ポイントのパラメーター (C++) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54b15d849efacb681eb8b4238cd067144bc67342
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Isolated Shell エントリ ポイントのパラメーター (C++)
Visual Studio シェル ベースのアプリケーションの開始時に、Visual Studio シェルの開始のエントリ ポイントを呼び出します。 シェルの開始のエントリ ポイントへの呼び出しでは、次の設定をオーバーライドできます。 各設定の説明は、次を参照してください。[です。Pkgdef ファイル](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)です。  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   AppName  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Visual Studio 分離シェル テンプレートは、ソース ファイルを作成*solutionName*.cpp、場所*solutionName*アプリケーションのソリューションの名前です。 このファイルは、_tWinMain 関数は、アプリケーションのメイン エントリ ポイントを定義します。 この関数は、シェルの開始のエントリ ポイントを起動します。  
  
 アプリケーションの起動時に、これらの設定を変更することによって、アプリケーションの動作を変更できます。  
  
## <a name="parameters"></a>パラメーター  
 Visual Studio シェルの開始のエントリ ポイントでは、5 つのパラメーターを定義します。 最初の 4 つのパラメーターを変更することはできません。 5 番目のパラメーターは、設定の上書きの一覧を取得します。 シェルの開始のエントリ ポイントは、アプリケーションのメイン エントリ ポイントから呼び出されます。  
  
 シェルの開始のエントリ ポイントには、次の署名があります。  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 アプリケーション設定をオーバーライドするには、設定の値のままにしたくない場合は、null のポインターとしてパラメーターをオーバーライドします。  
  
 1 つまたは複数の設定を無効にするには、オーバーライドされるように設定を含む Unicode 文字列を渡します。 文字列は、名前と値のペアのセミコロンで区切られた一覧を示します。 各ペアは、後に等号 (=)、その後に、設定を適用する値を無効にすると、設定の名前を表します。  
  
> [!NOTE]
>  Unicode 文字列に空白を含めないでください。  
  
 ブール値の設定は、次の文字列は値 true を表します。その他のすべての文字列では、値 false を表します。 これらの文字列は区別されません。  
  
-   \+  
  
-   1  
  
-   -1  
  
-   日付  
  
-   true  
  
-   可  
  
## <a name="example"></a>例  
 アドインを無効にして、アプリケーションの既定のプロジェクトの場所を変更する、"AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp"最後のパラメーターを設定できます。  
  
## <a name="see-also"></a>関連項目  
 [分離シェルのカスタマイズ](customizing-the-isolated-shell.md)   
 [.Pkgdef ファイル](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)