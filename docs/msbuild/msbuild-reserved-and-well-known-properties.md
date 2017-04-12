---
title: "MSBuild の予約済みおよび既知のプロパティ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 078576d6e1988bf1cefbb09646ea44f61085f5cf
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild の予約済みおよび既知のプロパティ
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] には、プロジェクト ファイルに関する情報と [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] のバイナリに関する情報を格納する一連の定義済みのプロパティが用意されています。 これらのプロパティは、他の [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロパティと同じように評価されます。 たとえば、`MSBuildProjectFile` プロパティを使用するには、「`$(MSBuildProjectFile)`」と入力します。  
  
 MSBuild は、次の表の値を使用して予約済みおよび既知のプロパティを事前に定義します。 予約されたプロパティはオーバーライドできませんが、既知のプロパティは同じ名前を持つ環境プロパティ、グローバル プロパティ、またはプロジェクト ファイルで宣言されたプロパティでオーバーライドできます。  
  
## <a name="reserved-and-well-known-properties"></a>予約済みのプロパティと既知のプロパティ  
 次の表では、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 予約済みプロパティについて説明します。  
  
|プロパティ|説明|予約または既知|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|現在使用されている [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] バイナリが格納されているフォルダーの絶対パス (C:\Windows\Microsoft.Net\Framework\\*versionNumber* など)。 このプロパティは、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ディレクトリのファイルを参照する必要がある場合に便利です。<br /><br /> このプロパティに最後の円記号を含めないでください。|予約されています。|  
|`MSBuildExtensionsPath`|.NET Framework 4 で導入: `MSBuildExtensionsPath` の既定値と `MSBuildExtensionsPath32` の既定値の間に違いはありません。 環境変数 `MSBUILDLEGACYEXTENSIONSPATH` を null 以外の値に設定すると、`MSBuildExtensionsPath` の既定値の動作を以前のバージョンで有効にすることができます。<br /><br /> .NET Framework 3.5 以前では、`MSBuildExtensionsPath` の既定値は、現在のプロセスのビット数に応じて、\Program Files\ フォルダーまたは \Program Files (x86) フォルダーの下にある MSBuild サブフォルダーのパスを指していました。 たとえば、64 ビット コンピューター上の 32 ビット プロセスの場合、このプロセスが指すのは \Program Files (x86) フォルダーです。 64 ビット コンピューター上の 64 ビット プロセスの場合、このプロセスが指すのは \Program Files フォルダーです。<br /><br /> このプロパティに最後の円記号を含めないでください。<br /><br /> この場所は、カスタム ターゲット ファイルを格納するために役立ちます。 たとえば、ターゲット ファイルを \Program Files\MSBuild\MyFiles\Northwind.targets にインストールし、次の XML でプロジェクト ファイルにインポートできます。<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|既知のプロパティ|  
|`MSBuildExtensionsPath32`|\Program Files フォルダーまたは \Program Files (x86) フォルダーの下にある [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] サブフォルダーのパス。 このパスは常に、32 ビット コンピューター上の 32 ビットの \Program Files フォルダー、および 64 ビット コンピューター上の \Program Files (x86) を指します。 `MSBuildExtensionsPath` および `MSBuildExtensionsPath64` も参照してください。<br /><br /> このプロパティに最後の円記号を含めないでください。|既知のプロパティ|  
`MSBuildExtensionsPath64`|\Program Files フォルダーの下にある [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] サブフォルダーのパス。 64 ビット コンピューターの場合、このパスは常に、\Program Files フォルダーを指します。 32 ビット コンピューターの場合、このパスは空白です。 `MSBuildExtensionsPath` および `MSBuildExtensionsPath32` も参照してください。<br /><br /> このプロパティに最後の円記号を含めないでください。|既知のプロパティ|  
|`MSBuildLastTaskResult`|前のタスクがエラーを発生することなく完了した場合は、(警告があった場合でも) `true` を返します。前のタスクでエラーが発生した場合は、`false` を返します。 通常、エラーがタスクで発生する場合、プロジェクト内ではエラーは最後に発生します。 したがって、このプロパティの値は、次のシナリオ以外では `false` にはなりません。<br /><br /> - [Task 要素 (MSBuild)](../msbuild/task-element-msbuild.md) の `ContinueOnError` の属性が `WarnAndContinue` (または `true`)、または `ErrorAndContinue` に設定されている場合。<br /><br /> - `Target` に、子要素として [OnError 要素 (MSBuild)](../msbuild/onerror-element-msbuild.md) がある場合。|予約されています。|  
|`MSBuildNodeCount`|ビルド時に使用する同時実行プロセスの最大数。 これは、コマンド ラインで **/maxcpucount** に指定した値です。 値を使用せずに **/maxcpucount** を指定した場合、`MSBuildNodeCount` はコンピューター上のプロセッサの数を示します。 詳細については、「[コマンドライン リファレンス](../msbuild/msbuild-command-line-reference.md)」と「[複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)」をご覧ください。|予約されています。|  
|`MSBuildProgramFiles32`|32 ビットのプログラム フォルダーの場所 (`C:\Program Files (x86)` など)。<br /><br /> このプロパティに最後の円記号を含めないでください。|予約されています。|  
|`MSBuildProjectDefaultTargets`|`DefaultTargets` 要素の `Project` 属性で指定されるターゲットの完全な一覧。 たとえば、次の `Project` 要素の `MSBuildDefaultTargets` プロパティの値は `A;B;C` となります。<br /><br /> `<Project DefaultTargets="A;B;C" >`|予約されています。|  
|`MSBuildProjectDirectory`|プロジェクト ファイルがあるディレクトリの絶対パス。`C:\MyCompany\MyProduct` のようになります。<br /><br /> このプロパティに最後の円記号を含めないでください。|予約されています。|  
|`MSBuildProjectDirectoryNoRoot`|ルート ドライブを除く `MSBuildProjectDirectory` のプロパティの値。<br /><br /> このプロパティに最後の円記号を含めないでください。|予約されています。|  
|`MSBuildProjectExtension`|ピリオドを含むプロジェクト ファイルの名前の拡張子。.proj のようになります。|予約されています。|  
|`MSBuildProjectFile`|ファイル名の拡張子を含むプロジェクト ファイルの完全なファイル名。MyApp.proj のようになります。|予約されています。|  
|`MSBuildProjectFullPath`|ファイル名の拡張子を含む、プロジェクト ファイルの絶対パスと完全なファイル名。C:\MyCompany\MyProduct\MyApp.proj のようになります。|予約されています。|  
|`MSBuildProjectName`|ファイル名の拡張子のないプロジェクト ファイルの名前。MyApp のようになります。|予約されています。|  
|`MSBuildStartupDirectory`|
          [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] が呼び出されるフォルダーの絶対パス。 このプロパティを使用すると、プロジェクト ツリーの特定の場所にすべての内容をビルドできます。各ディレクトリに dirs.proj ファイルを作成する必要はありません。 次の例に示すように、c:\traversal.proj という名前の 1 つのプロジェクトだけが作成されます。<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> ツリー上の任意の場所でビルドするには、次のように入力します。<br /><br /> `msbuild c:\traversal.proj`<br /><br /> このプロパティに最後の円記号を含めないでください。|予約されています。|  
|`MSBuildThisFile`|
          `MSBuildThisFileFullPath` のファイル名とファイル拡張子の部分。|予約されています。|  
|`MSBuildThisFileDirectory`|
          `MSBuildThisFileFullPath` のディレクトリの部分。<br /><br /> パスに最後の円記号を含めます。|予約されています。|  
|`MSBuildThisFileDirectoryNoRoot`|
          `MSBuildThisFileFullPath` のディレクトリの部分 (ルート ドライブを除く)。<br /><br /> パスに最後の円記号を含めます。|予約されています。|  
|`MSBuildThisFileExtension`|
          `MSBuildThisFileFullPath` のファイル名拡張子の部分。|予約されています。|  
|`MSBuildThisFileFullPath`|実行中のターゲットを含むプロジェクト ファイルまたはターゲット ファイルの絶対パス。<br /><br /> ヒント：ターゲット ファイルに対して相対的であり、元のプロジェクト ファイルに対しては相対的ではない位置を示す、ターゲット ファイルの相対パスを指定できます。|予約されています。|  
|`MSBuildThisFileName`|
          `MSBuildThisFileFullPath` のファイル名の部分 (ファイル名拡張子を除く)。|予約されています。|  
|`MSBuildToolsPath`|
          [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] の値に関連付けられている `MSBuildToolsVersion` のバージョンのインストール パス。<br /><br /> パスに最後の円記号を含めません。<br /><br /> このプロパティはオーバーライドできません。|予約されています。|  
|`MSBuildToolsVersion`|プロジェクトのビルドに使用する [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ツールセットのバージョン。<br /><br /> メモ：[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ツールセットは、アプリケーションのビルドで使用するタスク、ターゲット、およびツールで構成されます。 ツールには、csc.exe や vbc.exe などのコンパイラが含まれます。 詳細については、「[MSBuild ツールセット (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)」と「[標準ツールセット構成とカスタム ツールセット構成](../msbuild/standard-and-custom-toolset-configurations.md)」をご覧ください。|予約されています。|  
  
## <a name="see-also"></a>関連項目  
 [MSBuild リファレンス](../msbuild/msbuild-reference.md)
 [MSBuild プロパティ](../msbuild/msbuild-properties.md)
