---
title: "方法: 既存の .Ctc ファイルから .Vsct ファイルを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT ファイル、.ctc ファイルに基づく作成"
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 方法: 既存の .Ctc ファイルから .Vsct ファイルを作成する
既存のコマンドテーブルの .ctc ソース ファイルから XML ベースの .vsct ファイルを作成できます。 これにより、新しい XML ベースの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コマンド テーブル \(VSCT\) コンパイラ形式を利用できます。  
  
### .ctc ファイルから .vsct ファイルを作成するには  
  
1.  Perl 言語のコピーを取得します。  
  
2.  通常は *\<Visual Studio SDK インストール パス\>*\\VisualStudioIntegration\\Tools\\bin フォルダーにある Perl スクリプト ConvertCTCToVSCT.pl のコピーを取得します。  
  
3.  変換する .ctc ソース ファイルのコピーを取得します。  
  
4.  同じディレクトリにファイルを配置します。  
  
5.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコマンド プロンプト ウィンドウで、そのディレクトリに移動します。  
  
6.  型  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     PkgCmd.ctc は .ctc ファイルの名前であり、PkgCmd.vsct は作成する .vsct ファイルの名前です。  
  
     新しい .vsct XML コマンド テーブル ソース ファイルが作成されます。 他の .vsct ファイルと同様に、Vsct.exe \(VSCT コンパイラ\) を使用してファイルをコンパイルできます。  
  
    > [!NOTE]
    >  XML コメントの書式を変更すると、.vsct ファイルの読みやすさを改善できます。  
  
## 参照  
 [方法: 作成します。Vsct ファイル](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)