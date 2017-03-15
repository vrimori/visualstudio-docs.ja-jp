---
title: "グラフィックス診断の Capture メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea21995d-0241-412e-8f62-600c3794247f
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# グラフィックス診断の Capture メソッド
ここにイントロダクションを挿入します。  
  
## capture メソッド  
 [!INCLUDE[win81](../debugger/includes/win81_md.md)] では、DirectX 11.2 のランタイムはグラフィックス診断のようなデバッグ ツールの代わりにグラフィックス情報を内部でキャプチャできます。これは*robust capture \(ロバスト キャプチャ\)* と呼ばれます。  DirectX のランタイムにこのサポートが追加される前は、特定の DirectX 関数呼び出しをインターセプトし、完了する DirectX へ呼び出しを転送する前に引数およびその他の情報を記録することによって、グラフィックス情報がキャプチャされていました。これは*legacy capture \(レガシー キャプチャ\)* と呼ばれます。  
  
 [!INCLUDE[win81](../debugger/includes/win81_md.md)] では、DirectX のランタイムのみでグラフィックス情報のキャプチャを行うため、DirectX 11.2 をサポートするためにレガシー キャプチャを更新する必要はありません。したがって、レガシー キャプチャの使用は推奨されていません。  ただし DirectX 11.2 のランタイムは [!INCLUDE[win81](../debugger/includes/win81_md.md)] より前のバージョンの Windows をサポートしないため、[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] では、[!INCLUDE[win8](../debugger/includes/win8_md.md)] および [!INCLUDE[win7](../debugger/includes/win7_md.md)] を対象とするアプリケーションのために、現在もレガシー キャプチャをサポートしています。  
  
 これらの 2 つのメソッドでは類似の情報を記録しており、グラフィックス情報をキャプチャする方法や、グラフィックス診断ツールの使用方法は変わりません。  
  
### ロバスト キャプチャ  
 ロバスト キャプチャは、[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]、[!INCLUDE[win81](../debugger/includes/win81_md.md)]、および Windows Phone 8.1 で [!INCLUDE[winblue_winrt_2](../debugger/includes/winblue_winrt_2_md.md)] のグラフィックス診断をサポートします。  DirectX 10.0 から DirectX 11.2 をサポートしており、タイル型リソースなどの Direct3D 11.2 の新機能に関するグラフィックス情報もキャプチャできます。  ただし、Direct3D 11.2 のすべての機能は完全にサポートしていません。たとえば、HLSL シェーダー リンキング機能を使用して作成された HLSL シェーダーはデバッグできません。  ロバスト キャプチャ は新しいキャプチャ API を使用して、プログラムによるキャプチャ シナリオをサポートします。  
  
### レガシー キャプチャ  
 レガシー キャプチャは[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]、Windows RT 8、および [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] で [!INCLUDE[win8](../debugger/includes/win8_md.md)] および [!INCLUDE[win7](../debugger/includes/win7_md.md)] のグラフィックス診断をサポートします。  これは DirectX 10.0 から DirectX 11.1 までをサポートしています。  レガシー キャプチャは Direct3D 11.2 の機能はサポートしていないため、ロバスト キャプチャを使用できないシナリオを除いては、レガシー キャプチャは推奨されていません。  レガシー キャプチャは `vsgcapture.h` ヘッダー ファイルに定義されているキャプチャ API を使用して、プログラムによるキャプチャ シナリオをサポートします。  このようなプログラムによるキャプチャも、ロバスト キャプチャを使用できないシナリオを除いては、推奨されていません。  
  
## 参照  
 [グラフィックス情報のキャプチャ](../debugger/capturing-graphics-information.md)   
 [チュートリアル: グラフィックス情報のキャプチャ](../debugger/walkthrough-capturing-graphics-information.md)