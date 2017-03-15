---
title: "分離シェル エントリ ポイントのパラメーター (C++) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 10
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
ms.openlocfilehash: 13f05a147f0d9ab36d49b93cc91bcbaa7b002c70
ms.lasthandoff: 02/22/2017

---
# <a name="isolated-shell-entry-point-parameters-c"></a>分離シェル エントリ ポイントのパラメーター (C++)
Visual Studio シェルベースのアプリケーションの起動時に、Visual Studio シェルの開始のエントリ ポイントを呼び出します。 シェルの開始のエントリ ポイントへの呼び出しでは、次の設定をオーバーライドできます。 各設定については、次を参照してください。[します。Pkgdef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)します。  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   アプリ名  
  
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
  
 Visual Studio シェルの分離のテンプレートは、ソース ファイルを作成*solutionName*.cpp、場所*solutionName*アプリケーションのソリューション名です。 このファイルは、_tWinMain 関数は、アプリケーションのメイン エントリ ポイントを定義します。 この関数は、シェルの開始のエントリ ポイントを呼び出します。  
  
 アプリケーションの起動時に、これらの設定を変更することで、アプリケーションの動作を変更できます。  
  
## <a name="parameters"></a>パラメーター  
 Visual Studio シェルの開始のエントリ ポイントでは、5 つのパラメーターを定義します。 最初の&4; つのパラメーターは変更されません。 5 番目のパラメーターは、設定の上書きの一覧を取得します。 シェルの開始のエントリ ポイントは、アプリケーションのメイン エントリ ポイントから呼び出されます。  
  
 シェルの開始のエントリ ポイントには、次のシグネチャが含まれています。  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 アプリケーション設定をオーバーライドするには、設定の値のままにしたくない場合は、null ポインターとしてパラメーターを上書きします。  
  
 1 つまたは複数の設定を無効にするには、オーバーライドする設定を含む Unicode 文字列を渡します。 文字列は、名前と値のペアのセミコロンで区切った一覧を示します。 各ペアは、等号 (=) の設定を適用する値の後に続くを無効にする設定の名前を表します。  
  
> [!NOTE]
>  Unicode 文字列では、空白文字を含めないでください。  
  
 ブール値の設定は、次の文字列は値 true を表します。その他のすべての文字列は、値 false を表します。 これらの文字列が区別されます。  
  
-   \+  
  
-   1  
  
-   -1  
  
-   日付  
  
-   true  
  
-   可  
  
## <a name="example"></a>例  
 アドインを無効にして、アプリケーションの既定のプロジェクトの場所を変更する、"AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp"の最後のパラメーターを設定することができます。  
  
## <a name="see-also"></a>関連項目  
 [分離シェルをカスタマイズします。](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgdef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
