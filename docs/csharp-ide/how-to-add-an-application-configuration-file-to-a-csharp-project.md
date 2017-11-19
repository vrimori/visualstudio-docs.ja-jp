---
title: "方法: c# プロジェクトに、アプリケーション構成ファイルを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 097e7a2eac78fe85b2a3ab62d5cdf1fd18908d56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>方法: C# プロジェクトにアプリケーション構成ファイルを追加する
アプリケーション構成ファイル (app.config) を c# プロジェクトに追加すると、共通言語ランタイムの特定し、アセンブリ ファイルを読み込みますをカスタマイズできます。 アプリケーション構成ファイルの詳細については、次を参照してください。[ランタイムがアセンブリを検索する方法](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)です。  
  
> [!NOTE]
>  UWP アプリには、app.config テンプレートが含まれていません。
  
 プロジェクトをビルドするときに、開発環境は、app.config ファイルを自動的にコピー、実行可能ファイルの一致するように、コピーのファイル名を変更し、bin ディレクトリにコピーを移動します。  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>C# プロジェクトに、アプリケーション構成ファイルを追加するには  
  
1.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
2.  展開**インストール**、展開**Visual c# アイテム**を選択し、**アプリケーション構成ファイル**テンプレート。  
  
3.  **名前**テキスト ボックスは、名前を入力しを選択し、**追加**ボタンをクリックします。  
  
     App.config というファイルがプロジェクトに追加されます。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーションの設定の管理 (.NET)](../ide/managing-application-settings-dotnet.md)   
 [構成ファイル スキーマ](/dotnet/framework/configure-apps/file-schema/index)   
 [アプリの構成](/dotnet/framework/configure-apps/index)   
 [方法: .NET Framework のバージョンを対象とするアプリを構成します。](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Visual C# 開発環境の使用](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)