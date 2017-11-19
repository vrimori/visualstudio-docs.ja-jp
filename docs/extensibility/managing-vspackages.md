---
title: "Vspackage の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55ba59a5a29181dfa3cdd70427720293582a648d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="managing-vspackages"></a>Vspackage の管理
ほとんどの場合、Vspackage を管理するプロジェクトと項目テンプレートが登録し、自動的にパッケージを読み込むためについて心配する必要はありません。 ただし、状況によっては、パッケージを管理するために少しを学習する必要があります。  
  
## <a name="using-the-experimental-instance"></a>実験用インスタンスを使用します。  
 実験用インスタンスの詳細についてを参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)です。  
  
## <a name="registering-and-unregistering-vspackages"></a>Vspackage の登録および登録解除しています  
 登録し、Vspackage とその他の種類の拡張機能の登録を解除する方法を調べるには、次を参照してください。[の登録および登録解除 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)です。  
  
## <a name="loading-a-vspackage"></a>VSPackage を読み込む  
 Vspackage は、CMDUICONTEXT GUID がオンになっている特定の自動読み込みを設定できます。 詳細については、次を参照してください。[読み込み Vspackage](../extensibility/loading-vspackages.md)です。  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>AsyncPackage を使用して、バック グラウンドで Vspackage をロードするには  
 AsyncPackage クラスには、Visual Studio での UI の応答性の向上のためのバック グラウンド スレッドで読み込みパッケージができるようにします。 詳細については、次を参照してください。[する方法: バック グラウンドで読み込み Vspackage を使用して AsyncPackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)です。  
  
## <a name="rule-based-ui-context-for-extensions"></a>拡張機能のコンテキストをルール ベースの UI  
 ルール ベースの UI コンテキストにより、拡張機能の作成者にする UI コンテキストがアクティブになり、関連付けられている Vspackage が読み込まれる正確な条件を定義します。 詳細については、次を参照してください。[する方法: Visual Studio 拡張機能の使用規則ベースの UI コンテキスト](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)です。  
  
## <a name="diagnosing-extension-performance"></a>拡張機能のパフォーマンスを診断します。  
拡張機能の起動とソリューションの読み込みのパフォーマンスに影響します。 Visual Studio 拡張機能への影響を計算する方法およびどのように分析できますローカルで拡張機能がパフォーマンスに影響する拡張機能として表示されるかどうかを説明します。 詳細については、次を参照してください。[する方法: 診断拡張機能のパフォーマンス](how-to-diagnose-extension-performance.md)です。 
  
## <a name="troubleshooting-vspackages"></a>Vspackage のトラブルシューティング  
 ロードまたはエラーが発生する Vspackage をトラブルシューティングするためのテクニックを調べる: [Vspackage のトラブルシューティング](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)