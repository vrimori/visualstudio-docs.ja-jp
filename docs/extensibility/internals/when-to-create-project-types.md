---
title: "プロジェクトの種類を作成する場合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクトの種類を作成するための条件"
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# プロジェクトの種類を作成する場合
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

新しいプロジェクトを作成するとユーザーの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をカスタマイズするための基本機能を提供します。  ただし新しいプロジェクトを作成すると[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のすべてのカスタマイズは必要ではありません。  次のガイドラインでは新しいプロジェクトでのシナリオに必要かどうかを判断する必要があります。  
  
## 新しいプロジェクトを作成します。  
 次の一つ以上で動作するように [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をカスタマイズする場合はプロジェクトを作成する必要があります :  
  
-   加わりましたり構成およびビルド ソース管理はに配置します。  
  
-   はデバッグのサポート。  
  
-   **ソリューション エクスプローラー**  のプロジェクト項目。  
  
-   **プロジェクトを開く**  または \[ENT2ENT\] ダイアログ ボックスを使用します。  
  
-   サポートプロジェクトの入れ子。  
  
## 既存のプロジェクトの種類を拡張します。  
 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] プロジェクトのビルド処理を変更する既存のプロジェクト タイプの動作を変更または拡張する場合などに [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を次のように使用できる新しいプロジェクトを作成するかも知れません :  
  
-   一つの単位として複数のファイルを使用します。  
  
-   サブ項目の階層で一つのファイルが表示されます。  
  
-   エディターで囲むコマンドのコンテキストを表示します。  
  
-   エディターのサービス コンテキストを表示します。  
  
## 既存のプロジェクトを使用します。  
 新しいプロジェクトを作成することは必要ではありません。  次の表はプロジェクトの種類を作成する必要がないするタスクを示しています。  
  
|タスク|Description|  
|---------|-----------------|  
|コマンドの処理|VSPackage でもコマンドを処理できます。|  
|エディターのビルド|カスタム エディターを登録できます。  詳細については、「[Document Windows and Editors](http://msdn.microsoft.com/ja-jp/603625e1-62b6-413a-bc44-089346e166bc)」を参照してください。|  
|ウィンドウの所有|新しいプロジェクトを追加せずにツール ウィンドウとドキュメント ウィンドウを作成できます。|  
|\[プロパティ\] ウィンドウのプロパティの公開|すべてのオブジェクトがプロパティを公開できます。|  
  
## プロジェクトのサブタイプを作成します。  
 新しいプロジェクトを作成しなくてもマネージ プロジェクトの種類を拡張するにはプロジェクトのサブタイプを使用できます。  プロジェクトのサブタイプはMicrosoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] または  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] で記述されたマネージ プロジェクトを拡張するために COM の集計を使用します。  COM の集計を使用してもマネージ プロジェクトのシステムの実装の大部分を再利用して特定のシナリオにインターフェイスをサポートする集計を使用してカスタマイズできます。  プロジェクトの一部の種類の詳細については[プロジェクトのサブタイプ](../../extensibility/internals/project-subtypes.md) を参照してください。  
  
## 参照  
 [Document Windows and Editors](http://msdn.microsoft.com/ja-jp/603625e1-62b6-413a-bc44-089346e166bc)   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)