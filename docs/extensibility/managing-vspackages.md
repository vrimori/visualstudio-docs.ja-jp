---
title: "Vspackage を管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>Vspackage を管理します。
ほとんどの場合プロジェクトおよび項目テンプレートの登録し、パッケージを自動的に読み込みため vspackages にあるの管理について心配する必要はありません。 ただし、状況によっては、パッケージを管理するためにさらに詳しくを学習する必要があります。  
  
## <a name="using-the-experimental-instance"></a>実験用インスタンスを使用します。  
 実験用インスタンスの詳細を参照してください[の実験用インスタンス](../extensibility/the-experimental-instance.md)します。  
  
## <a name="registering-and-unregistering-vspackages"></a>Vspackage の登録と登録解除しています  
 登録し、Vspackage およびその他の種類の拡張機能の登録を解除する方法については、次を参照してください。[の登録および登録解除 VSPackages](../extensibility/registering-and-unregistering-vspackages.md)します。  
  
## <a name="loading-a-vspackage"></a>VSPackage を読み込む  
 VSPackages は、CMDUICONTEXT GUID がオンになっている特定の自動読み込みを設定できます。 詳細については、次を参照してください。[読み込み VSPackages](../extensibility/loading-vspackages.md)します。  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>AsyncPackage を使用して、バック グラウンドで VSPackages をロードするには  
 AsyncPackage クラスは、パッケージが Visual Studio での UI の応答性の向上のバック グラウンド スレッドでの読み込みを許可します。 詳細については、次を参照してください。[方法: バック グラウンドで読み込み VSPackages に使用する AsyncPackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)します。  
  
## <a name="rule-based-ui-context-for-extensions"></a>拡張機能の UI のルールに基づくコンテキスト  
 UI のルールに基づくコンテキストは、拡張機能の作成者にする UI コンテキストがアクティブになり、関連付けられている Vspackage が読み込まれる正確な条件を定義できます。 詳細については、次を参照してください。[方法: Visual Studio 拡張機能の UI コンテキストを使用する規則に基づく](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)します。  
  
## <a name="diagnosing-extension-performance"></a>拡張機能のパフォーマンスを診断します。  
拡張機能は、起動とソリューションの読み込みのパフォーマンスに影響します。 Visual Studio 拡張機能への影響を計算する方法と、それが分析される方法ローカルで拡張機能が拡張機能に影響を与えるパフォーマンスとして表示されるかどうかを説明します。 詳細については、次を参照してください。[方法: 診断拡張機能のパフォーマンス](how-to-diagnose-extension-performance.md)します。 
  
## <a name="troubleshooting-vspackages"></a>Vspackage のトラブルシューティング  
 Vspackage が読み込まれないように、またはエラーが発生するをトラブルシューティングするためのテクニックを調べる: [VSPackages のトラブルシューティング](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>関連項目  
 [Vspackages にあります。](../extensibility/internals/vspackages.md)
