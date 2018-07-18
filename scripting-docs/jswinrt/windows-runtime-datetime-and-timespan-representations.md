---
title: Windows ランタイムの DateTime と TimeSpan 表現 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime dates and times
- TimeSpan [JavaScript]
- DateTime [JavaScript]
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d7c394b57eb0215e3dff857d935b367e602c2b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571422"
---
# <a name="windows-runtime-datetime-and-timespan-representations"></a>Windows ランタイムの DateTime と TimeSpan 表現
JavaScript での日付と時刻の表現は、Windows ランタイム バージョンでの表現とは異なります。 Windows ランタイムの [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) 構造は、JavaScript では、`DateTime` データと一致する (ただし、JavaScript `Date` とは範囲と精度が異なる) バッキング ストアを持つ [Date](../javascript/reference/date-object-javascript.md) として表現されます。 このカスタム `Date` オブジェクトを変更すると、JavaScript の標準 `Date` となり、精度が失われます。 JavaScript の `Date` 値は、Windows ランタイムの `DateTime` に渡すことができます。その場合、範囲のチェックが行われるため、マーシャリング例外が発生する場合もあります。  
  
 Windows ランタイムの [TimeSpan](http://msdn.microsoft.com/en-us/c5defb66-819c-4796-85b5-07ed249a5d86) 構造は、ミリ秒に変換され、JavaScript の数値として返されます。  
  
## <a name="see-also"></a>関連項目  
 [JavaScript での Windows ランタイムの使用](../jswinrt/using-the-windows-runtime-in-javascript.md)