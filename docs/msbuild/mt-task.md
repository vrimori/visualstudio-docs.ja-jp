---
title: "MT Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManifestTool.ResourceOutputFileName"
  - "VC.Project.VCManifestTool.SuppressDependencyElement"
  - "VC.Project.VCManifestTool.ManifestFromManagedAssembly"
  - "VC.Project.VCManifestTool.GenerateCategoryTags"
  - "VC.Project.VCManifestTool.EnableDPIAwareness"
  - "vc.task.mt"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBUILD (Visual C++), MT task"
  - "MT task (MSBuild (Visual C++))"
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# MT Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft マニフェスト ツール \(mt.exe\) をラップします。  詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」を参照してください。  
  
## パラメーター  
 **MT** タスクのパラメーターの説明を次の表に示します。  タスク パラメーターの大部分、およびいくつかのパラメーター セットは、コマンド ライン オプションに対応します。  
  
> [!NOTE]
>  mt.exe のドキュメントでは、ハイフン \(**\-**\) をコマンド ライン オプションのプレフィックスとして使用していますが、このトピックでは、スラッシュ \(**\/**\) を使用しています。  どちらのプレフィックスも使用できます。  
  
|パラメーター|Description|  
|------------|-----------------|  
|**AdditionalManifestFiles**|省略可能な **String\[\]** 型のパラメーターです。<br /><br /> 1 つ以上のマニフェスト ファイルの名前を指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/manifest** オプションの説明を参照してください。|  
|**AdditionalOptions**|省略可能な **String** 型のパラメーターです。<br /><br /> コマンド ライン オプションのリストです。  たとえば、"*\/option1 \/option2 \/option\#*" のように指定します。  他の **MT** タスク パラメーターでは表されないコマンド ライン オプションを指定する場合は、このパラメーターを使用します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」を参照してください。|  
|**AssemblyIdentity**|省略可能な **String** 型のパラメーターです。<br /><br /> マニフェストの **assemblyIdentity** 要素の属性値を指定します。  コンマ区切りのリストを指定します。最初の構成要素は `name` 属性の値で、その後に、名前と値のペアを *\<attribute name\>\=\<attribute\_value\>* の形式で 1 つ以上指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/identity** オプションの説明を参照してください。|  
|**ComponentFileName**|省略可能な **String** 型のパラメーターです。<br /><br /> .rgs ファイルまたは .tlb ファイルからビルドするダイナミック リンク ライブラリの名前を指定します。  **RegistrarScriptFile** MT タスク パラメーターまたは **TypeLibraryFile** MT タスク パラメーターを指定する場合、このパラメーターは必須です。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/dll** オプションの説明を参照してください。|  
|**DependencyInformationFile**|省略可能な **String** 型のパラメーターです。<br /><br /> マニフェスト ツールのビルド依存関係情報を追跡するために Visual Studio で使用される依存関係情報ファイルを指定します。|  
|**EmbedManifest**|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、マニフェスト ファイルをアセンブリに埋め込みます。  `false` の場合は、スタンドアロン マニフェスト ファイルとして作成します。|  
|**EnableDPIAwareness**|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、アプリケーションを DPI 対応として指定するマニフェスト情報を追加します。  DPI 対応のアプリケーションを作成すると、さまざまな高解像度設定でユーザー インターフェイスの外観を統一できます。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「High DPI \(高 DPI\)」を参照してください。|  
|**GenerateCatalogFiles**|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、カタログ定義 \(.cdf\) ファイルを生成します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/makecdfs** オプションの説明を参照してください。|  
|**GenerateCategoryTags**|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、カテゴリのタグが生成されます。  このパラメーターを `true` にする場合、**ManifestFromManagedAssembly MT** タスク パラメーターも指定する必要があります。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/category** オプションの説明を参照してください。|  
|**InputResourceManifests**|省略可能な **String** 型のパラメーターです。<br /><br /> 指定した ID を持つ RT\_MANIFEST 型のリソースからマニフェストを入力します。  リソースは、*\<file\>\[***;***\[***\#***\]\<resource\_id\>\]* の形式で指定します。`resource_id` は省略可能なパラメーターで、負でない 16 ビットの数値です。<br /><br /> `resource_id` が指定されていない場合、CREATEPROCESS\_MANIFEST\_RESOURCE の既定値 \(1\) が使用されます。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/inputresource** オプションの説明を参照してください。|  
|**ManifestFromManagedAssembly**|省略可能な **String** 型のパラメーターです。<br /><br /> 指定したマネージ アセンブリからマニフェストを生成します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/managedassemblyname** オプションの説明を参照してください。|  
|**ManifestToIgnore**|省略可能な **String** 型のパラメーターです。<br /><br /> \(使用しません\)。|  
|**OutputManifestFile**|省略可能な **String** 型のパラメーターです。<br /><br /> 出力マニフェストの名前を指定します。  このパラメーターを省略し、操作対象のマニフェストが 1 つだけの場合、そのマニフェストがそのまま変更されます。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/out** オプションの説明を参照してください。|  
|**OutputResourceManifests**|省略可能な **String** 型のパラメーターです。<br /><br /> 指定した ID を持つ RT\_MANIFEST 型のリソースにマニフェストを出力します。  リソースは、*\<file\>\[***;***\[***\#***\]\<resource\_id\>\]* の形式で指定します。`resource_id` は省略可能なパラメーターで、負でない 16 ビットの数値です。<br /><br /> `resource_id` が指定されていない場合、CREATEPROCESS\_MANIFEST\_RESOURCE の既定値 \(1\) が使用されます。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/outputresource** オプションの説明を参照してください。|  
|**RegistrarScriptFile**|省略可能な **String** 型のパラメーターです。<br /><br /> 登録を必要としない COM マニフェストのサポートに使用するレジストラー スクリプト \(.rgs\) ファイルの名前を指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/rgs** オプションの説明を参照してください。|  
|**ReplacementsFile**|省略可能な **String** 型のパラメーターです。<br /><br /> レジストラー スクリプト \(.rgs\) ファイル内の置換可能な文字列の値が格納されているファイルを指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/replacements** オプションの説明を参照してください。|  
|**ResourceOutputFileName**|省略可能な **String** 型のパラメーターです。<br /><br /> プロジェクト出力へのマニフェストの埋め込みに使用される出力リソース ファイルを指定します。|  
|**Sources**|省略可能な `ITaskItem[]` 型のパラメーターです。<br /><br /> スペース区切りのマニフェスト ソース ファイルのリストを指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/manifest** オプションの説明を参照してください。|  
|**SuppressDependencyElement**|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、dependency 要素を使用せずにマニフェストを生成します。  このパラメーターを `true` にする場合、**ManifestFromManagedAssembly MT** タスク パラメーターも指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/nodependency** オプションの説明を参照してください。|  
|**SuppressStartupBanner**|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、タスクの開始時に著作権およびバージョン番号のメッセージが表示されないようにします。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/nologo** オプションの説明を参照してください。|  
|**TrackerLogDirectory**|省略可能な `String` 型のパラメーターです。<br /><br /> このタスクの追跡ログを格納する中間ディレクトリを指定します。|  
|**TypeLibraryFile**|省略可能な **String** 型のパラメーターです。<br /><br /> タイプ ライブラリ \(.tlb\) ファイルの名前を指定します。  このパラメーターを指定する場合、**ComponentFileName MT** タスク パラメーターも指定します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/tlb** オプションの説明を参照してください。|  
|**UpdateFileHashes**|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、**UpdateFileHashesSearchPath MT** タスク パラメーターで指定されているパスのファイルのハッシュ値を計算し、その計算値を使用して、マニフェストの **file** 要素の **hash** 属性の値を更新します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/hashupdate** オプションの説明を参照してください。  また、この表の **UpdateFileHashesSearchPath** パラメーターの説明も参照してください。|  
|**UpdateFileHashesSearchPath**|省略可能な `String` 型のパラメーターです。<br /><br /> ファイルのハッシュを更新するときに使用する検索パスを指定します。  このパラメーターは **UpdateFileHashes MT** タスク パラメーターと共に使用します。<br /><br /> 詳細については、この表の **UpdateFileHashes** パラメーターの説明を参照してください。|  
|**VerboseOutput**|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、詳細なデバッグ情報を表示します。<br /><br /> 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Mt.exe \(Mt.exe\)」の **\/verbose** オプションの説明を参照してください。|  
  
## 解説  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)