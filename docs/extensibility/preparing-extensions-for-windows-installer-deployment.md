---
title: "Windows インストーラーの配置の拡張機能を準備します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "vsix msi"
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Windows インストーラーの配置の拡張機能を準備します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows インストーラー パッケージ \(MSI\) を使用して、VSIX パッケージを展開することはできません。 ただし、MSI の展開用の VSIX パッケージの内容を抽出することができます。 このドキュメントでは、プロジェクトの既定の出力は、セットアップ プロジェクトに組み込むのための VSIX パッケージを準備する方法を示します。  
  
## Windows インストーラーの配置の拡張機能プロジェクトを準備します。  
 セットアップ プロジェクトに追加する前に、新しい拡張機能プロジェクトでこれらの手順を実行します。  
  
#### Windows インストーラーの配置の拡張機能プロジェクトを準備するには  
  
1.  VSPackage、MEF コンポーネント、エディターの表示要素または VSIX マニフェストを含むその他の機能拡張プロジェクトの種類を作成します。  
  
2.  VSIX マニフェストは、コード エディターで開きます。  
  
3.  設定する VSIX マニフェストの InstalledByMsi 要素 `true`します。 VSIX マニフェストに関する詳細については、次を参照してください。 [VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)します。  
  
     これは VSIX インストーラーが、コンポーネントをインストールしようとすることを防止できます。  
  
4.  プロジェクトを右クリックして **ソリューション エクスプ ローラー** \] をクリック **プロパティ**します。  
  
5.  選択、 **VSIX** \] タブをクリックします。  
  
6.  チェック ボックスを **次の場所にコピー VSIX コンテンツ** セットアップ プロジェクトは、ファイルを集荷するパスを入力します。  
  
## 既存の VSIX パッケージからファイルを抽出  
 ソース ファイルがあるないときに、セットアップ プロジェクトに既存の VSIX パッケージのコンテンツを追加する手順を実行します。  
  
#### 既存の VSIX パッケージからファイルを抽出するには  
  
1.  名前を変更します。VSIX ファイルから拡張を含む *filename*に .vsix *filename*.zip します。  
  
2.  .Zip ファイルの内容をディレクトリにコピーします。  
  
3.  \[Content\_types\] .xml ファイルをディレクトリから削除します。  
  
4.  前の手順で示すように、VSIX マニフェストを編集します。  
  
5.  残りのファイルをセットアップ プロジェクトに追加します。  
  
## 参照  
 [Visual Studio Installer Deployment](http://msdn.microsoft.com/ja-jp/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Walkthrough: Creating a Custom Action](http://msdn.microsoft.com/ja-jp/4bd4b63a-2b91-431e-839c-5752443f0eaf)