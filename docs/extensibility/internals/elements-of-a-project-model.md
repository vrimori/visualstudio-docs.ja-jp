---
title: "プロジェクト モデルの要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Visual Studio SDK] 実装に関する注意点"
  - "プロジェクト モデル"
  - "プロジェクト [Visual Studio SDK] 要素"
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# プロジェクト モデルの要素
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のすべてのプロジェクトとインターフェイスの実装は基本的な構造を共有しています : プロジェクトの種類のプロジェクト モデル。  VSPackage であるプロジェクト モデルでは開発している場合IDE によって提供されるグローバルな機能とともにデザインの決定と作業に基づいてオブジェクトを作成します。  たとえばプロジェクト項目がどのように保持するかを制御できますがファイルが保持する必要があるコントロール通知します。  ユーザーが開いているプロジェクト項目にフォーカスを設定し[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のメニュー バーの ENT1ENT \[入力\] メニューの  **保存**  を選択するとプロジェクト コードはファイルが変更されないようにIDE からコマンドを傍受しファイルを保持しIDE に通知を返します。  
  
 VSPackage はIDE のインターフェイスへのアクセスを提供するサービスして IDE とやり取りします。  たとえば特定のサービスによって監視しコマンドをルーティングしてプロジェクトで行った選択にコンテキスト情報を提供します。  VSPackage に必要なすべてのグローバル IDE 機能のサービスによって提供されます。  サービスの詳細については[方法: サービスを取得](../Topic/How%20to:%20Get%20a%20Service.md) を参照してください。  
  
 他の実装に関する考慮事項 :  
  
-   一つのプロジェクト モデルは複数のプロジェクトを含めることができます。  
  
-   プロジェクトの種類および付随のプロジェクト ファクトリは GUID で個別に登録されます。  
  
-   各プロジェクトにはユーザーが [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の UI で新しいプロジェクトを作成するときにテンプレート ウィザードで新しいファイルまたはプロジェクト ファイルを初期化する必要があります。  たとえば .vcproj ファイルには最終的な [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] テンプレートを初期化します。  
  
 次の図は標準的なプロジェクト構成を実現する主要インターフェイスサービスおよびオブジェクトを示します。  基になるオブジェクトなどのプログラミングの定型を作成するにはアプリケーションのヘルパー HierUtil7 を使用できます。  アプリケーション HierUtil7 ヘルパーに関する詳細については[Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/ja-jp/a5c16a09-94a2-46ef-87b5-35b815e2f346) を参照してください。  
  
 ![Visual Studio プロジェクト モデル グラフィック](../../extensibility/internals/media/vsprojectmodel.png "vsProjectModel")  
プロジェクト モデル  
  
 ダイアグラムに含まれないこの図でそのほかの省略可能なインターフェイスについての詳細が記載されているインターフェイスおよびサービス [プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md) を参照してください。  
  
 このプロジェクトではコマンドのコンテキストの GUID によってコマンド ルーティングに参加するコマンドをサポートし<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> のインターフェイスを実装する必要があります。  
  
## 参照  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/ja-jp/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)   
 [プロジェクトのファクトリを使用して、プロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [方法: サービスを取得](../Topic/How%20to:%20Get%20a%20Service.md)   
 [プロジェクトの種類を作成します。](../../extensibility/internals/creating-project-types.md)