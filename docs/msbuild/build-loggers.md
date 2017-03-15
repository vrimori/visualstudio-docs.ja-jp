---
title: "ビルド ロガー | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 11
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
ms.openlocfilehash: b28a3a7d7412a496802a176f6365e961cd7c2673
ms.lasthandoff: 02/22/2017

---
# <a name="build-loggers"></a>ビルド ロガー
ロガーを使うと、ビルドの出力をカスタマイズして、特定のビルド イベントに対する応答のメッセージ、エラー、または警告を表示できます。 各ロガーは、Microsoft.Build.Framework.dll アセンブリで定義されている <xref:Microsoft.Build.Framework.ILogger> インターフェイスを実装する .NET クラスとして実装されます。  
  
 ロガーを実装するには&2; つの方法があります。  
  
-   <xref:Microsoft.Build.Framework.ILogger> インターフェイスを直接実装します。  
  
-   Microsoft.Build.Utilities.dll アセンブリで定義されているヘルパー クラス <xref:Microsoft.Build.Utilities.Logger> からクラスを派生します。 <xref:Microsoft.Build.Utilities.Logger> は <xref:Microsoft.Build.Framework.ILogger> を実装し、一部の <xref:Microsoft.Build.Framework.ILogger> メンバーの既定の実装を提供します。  
  
 このトピックでは、<xref:Microsoft.Build.Utilities.Logger> を継承し、特定のビルド イベントに対する応答のメッセージをコンソールに表示する、簡単なロガーを作成する方法を説明します。  
  
## <a name="registering-for-events"></a>イベントの登録  
 ロガーの目的は、ビルド エンジンによって報告されたビルドの進行状況に関する情報を収集し、役に立つ方法でその情報を報告することです。 すべてのロガーは、イベントを登録する <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> メソッドを無視する必要があります。 次の例では、ロガーは <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>、<xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>、および <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> イベントを登録しています。  
  
 [!code-cs[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="responding-to-events"></a>イベントへの応答  
 特定のイベントを登録したロガーは、発生したイベントを処理する必要があります。 <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> および <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> イベントの場合、ロガーは短い語句と、イベントに関連するプロジェクト ファイルの名前を単に書き込みます。 ロガーからのすべてのメッセージは、コンソール ウィンドウに書き込まれます。  
  
 [!code-cs[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="responding-to-logger-verbosity-values"></a>ロガーの詳細値への応答  
 MSBuild.exe の **/verbosity** スイッチに特定の値が含まれる場合にのみ、イベントから情報を記録したいことがあります。 次の例の <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> イベント ハンドラーは、**/verbosity** スイッチによって設定される <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> プロパティが <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed` に等しい場合にのみ、メッセージを記録します。  
  
 [!code-cs[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specifying-a-logger"></a>ロガーの指定  
 ロガーがアセンブリにコンパイルされた後は、ビルドの間にそのロガーを使うように [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に指定する必要があります。 これは、MSBuild.exe で **/logger** スイッチを使って行います。 MSBuild.exe で使用可能なスイッチについて詳しくは、「[コマンド ライン リファレンス](../msbuild/msbuild-command-line-reference.md)」をご覧ください。  
  
 次のコマンド ラインは、プロジェクト `MyProject.csproj` をビルドし、`SimpleLogger.dll` で実装されているロガー クラスを使います。 **/nologo** スイッチはバナーと著作権のメッセージを非表示にし、**/noconsolelogger** スイッチは既定の [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] コンソール ロガーを無効にします。  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 次のコマンド ラインは同じロガーでプロジェクトをビルドしますが、`Verbosity` レベルは `Detailed` です。  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例には、ロガーの完全なコードが含まれます。  
  
### <a name="code"></a>コード  
 [!code-cs[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### <a name="comments"></a>コメント  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、コンソール ウィンドウに表示するのではなくファイルにログを書き込むロガーを実装する方法を示します。  
  
### <a name="code"></a>コード  
 [!code-cs[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
### <a name="comments"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild の概念](../msbuild/msbuild-concepts.md)
