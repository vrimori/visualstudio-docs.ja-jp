---
title: '方法: ドメイン固有言語の Namespace を変更する |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 19b756fb6957a22959614f63b93123f5cde817b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209028"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>方法: ドメイン固有言語の名前空間を変更する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ドメイン固有言語の名前空間を変更することができます。 変更を加える必要があります、 **DSL エクスプ ローラー**、Dsl パッケージ プロジェクトのプロパティおよびアセンブリ情報です。  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>ドメイン固有言語の名前空間を変更するには  
  
1.  **DSL エクスプ ローラー**、クリックして、 **Dsl**ノード。  
  
2.  **プロパティ**ウィンドウで、変更、 **Namespace**プロパティ。  
  
3.  ソリューションを保存し、テンプレートを変換します。  
  
4.  **プロジェクト** メニューのをクリックして**Dsl プロパティ**します。  
  
     プロジェクトのプロパティが表示されます。  
  
5.  **[アプリケーション]** タブをクリックします。  
  
6.  変更、**既定の名前空間**プロパティを新しい名前空間の名前。  
  
7.  アセンブリの名前を変更する場合は、変更、 **Assembly name プロパティです。**  
  
8.  アセンブリ名を変更した場合は、DslPackage\Package.tt を開き、この行を更新します。  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. カスタム コードを記述した場合は、コード ファイルの名前空間とクラス参照を変更することを確認してください。  
  
10. Visual Studio 実験用インスタンスをリセットします。  
  
    1.  削除**\Users\\**_{名}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  Windows で**開始**] メニューの [選択**すべてのプログラム**、 **Microsoft Visual Studio 2010 SDK**、**ツール**、**リセット、実験用インスタンス**します。  
  
11. **ビルド**] メニューの [選択**ソリューションのリビルド**します。  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



