---
title: "方法: ドメイン固有言語の Namespace を変更する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9fb477876f149e9e410e2dac34171e7581405524
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>方法: ドメイン固有言語の名前空間を変更する
ドメイン固有言語の名前空間を変更することができます。 変更を行う必要があります、 **DSL のエクスプ ローラー**、Dsl パッケージ プロジェクトのプロパティおよびアセンブリ情報です。  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>ドメイン固有言語の名前空間を変更するには  
  
1.  **DSL のエクスプ ローラー**をクリックして、 **Dsl**ノード。  
  
2.  **プロパティ**ウィンドウで、変更、 **Namespace**プロパティです。  
  
3.  ソリューションを保存し、テンプレートを変換します。  
  
4.  **プロジェクト** メニューのをクリックして**Dsl プロパティ**です。  
  
     プロジェクトのプロパティが表示されます。  
  
5.  **[アプリケーション]** タブをクリックします。  
  
6.  変更、**既定の名前空間**プロパティを新しい名前空間名。  
  
7.  アセンブリの名前を変更する場合は、変更、 **Assembly name プロパティです。**  
  
8.  アセンブリ名を変更した場合は、DslPackage\Package.tt を開き、次の行を更新します。  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. 任意のカスタム コードを記述した場合は、コード ファイルの名前空間とクラス参照を変更することを確認してください。  
  
10. Visual Studio 実験用インスタンスをリセットします。  
  
    1.  削除**\Users\\***、{name}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  Windows の**開始**] メニューの [選択**すべてのプログラム**、 **Microsoft Visual Studio 2010 SDK**、**ツール**、**リセット、実験用インスタンス**です。  
  
11. **ビルド**] メニューの [選択**ソリューションのリビルド**です。  
  
## <a name="see-also"></a>参照  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)