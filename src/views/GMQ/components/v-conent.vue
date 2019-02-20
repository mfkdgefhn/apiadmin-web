<template>
  <div>
    <row :gutter="5">
      <i-col v-for="item in vDate"
             :key="item.docno"
             :xs="24"
             :sm="12"
             :md="8"
             :lg="6"
             style="margin-bottom:5px">
        <Card class="img-center">
          <img style="height:200px;"
               :src="picUrl+item.productname+picJpg">
          <row>
            <i-col span="24">
              {{item.productname}}
            </i-col>
          </row>
          <row>
            <i-col span="6">
              销量排名
            </i-col>
            <i-col span="6">
              {{item.docn}}
            </i-col>
            <i-col span="6">
              期货订单
            </i-col>
            <i-col span="6">
              {{item.fwd}}
            </i-col>
          </row>
          <row>
            <i-col span="6">
              销量
            </i-col>
            <i-col span="6">
              {{item.saleqty}}
            </i-col>
            <i-col span="6">
              总发货
            </i-col>
            <i-col span="6">
              {{item.totqty}}
            </i-col>
          </row>
          <row>
            <i-col span="6">
              批发量
            </i-col>
            <i-col span="6">
              {{item.wholesaleqty}}
            </i-col>
            <i-col span="6">
              库存量
            </i-col>
            <i-col span="6">
              {{item.fastorageqty}}
            </i-col>
          </row>
          <row>
            <i-col span="6">
              售馨率
            </i-col>
            <i-col span="6">
              {{item.strate}}
            </i-col>
            <i-col span="6">
              成交价
            </i-col>
            <i-col span="6">
              {{item.priceactual}}
            </i-col>
          </row>
          <row>
            <i-col span="6">
              铺店数
            </i-col>
            <i-col span="6">
              {{item.fastoreqty}}
            </i-col>
            <i-col span="6">
              销店数
            </i-col>
            <i-col span="6">
              {{item.retailstoreqty}}
            </i-col>
          </row>
          <row>
            <i-col span="6">
              余货
            </i-col>
            <i-col span="6">
              {{item.qtyrem}}
            </i-col>
            <i-col span="6">
              动销率
            </i-col>
            <i-col span="6">
              {{item.dprate}}
            </i-col>
          </row>
        </Card>
      </i-col>
    </row>
  </div>
</template>

<script>
export default {
    computed: {
        picUrl () {
            return 'http://10.10.1.32:8018/Images/sku/';
        },
        picJpg () {
            return '.jpg';
        }
    },
    data () {
        return {
            vDate: [
                {
                    'wholesaleqty': '0',
                    'dprate': '.58',
                    'qtyrem': '0',
                    'retailstoreqty': '39',
                    'fastorageqty': '1867',
                    'sql2': '0',
                    'fwd': '0',
                    'strate': '.03',
                    'docn': '1',
                    'productname': '177510703',
                    'totqty': '0',
                    'priceactual': '233',
                    'saleqty': '48',
                    'fastoreqty': '67'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.53',
                    'qtyrem': '0',
                    'retailstoreqty': '36',
                    'fastorageqty': '1359',
                    'sql2': '.02',
                    'fwd': '936',
                    'strate': '.03',
                    'docn': '2',
                    'productname': '177110007',
                    'totqty': '1584',
                    'priceactual': '218',
                    'saleqty': '36',
                    'fastoreqty': '68'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.54',
                    'qtyrem': '0',
                    'retailstoreqty': '37',
                    'fastorageqty': '1291',
                    'sql2': '.02',
                    'fwd': '720',
                    'strate': '.03',
                    'docn': '3',
                    'productname': '177110009',
                    'totqty': '1606',
                    'priceactual': '237',
                    'saleqty': '36',
                    'fastoreqty': '68'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.5',
                    'qtyrem': '0',
                    'retailstoreqty': '34',
                    'fastorageqty': '1741',
                    'sql2': '.02',
                    'fwd': '840',
                    'strate': '.02',
                    'docn': '4',
                    'productname': '177110072',
                    'totqty': '1673',
                    'priceactual': '217',
                    'saleqty': '33',
                    'fastoreqty': '68'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.56',
                    'qtyrem': '0',
                    'retailstoreqty': '35',
                    'fastorageqty': '1201',
                    'sql2': '0',
                    'fwd': '0',
                    'strate': '.02',
                    'docn': '5',
                    'productname': '177510718',
                    'totqty': '0',
                    'priceactual': '236',
                    'saleqty': '30',
                    'fastoreqty': '63'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.45',
                    'qtyrem': '0',
                    'retailstoreqty': '30',
                    'fastorageqty': '2118',
                    'sql2': '0',
                    'fwd': '0',
                    'strate': '.01',
                    'docn': '6',
                    'productname': '177510713',
                    'totqty': '0',
                    'priceactual': '214',
                    'saleqty': '22',
                    'fastoreqty': '66'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.41',
                    'qtyrem': '0',
                    'retailstoreqty': '26',
                    'fastorageqty': '588',
                    'sql2': '.02',
                    'fwd': '360',
                    'strate': '.03',
                    'docn': '7',
                    'productname': '177110093',
                    'totqty': '780',
                    'priceactual': '215',
                    'saleqty': '19',
                    'fastoreqty': '64'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.47',
                    'qtyrem': '0',
                    'retailstoreqty': '15',
                    'fastorageqty': '699',
                    'sql2': '0',
                    'fwd': '0',
                    'strate': '.03',
                    'docn': '8',
                    'productname': '177510701',
                    'totqty': '0',
                    'priceactual': '236',
                    'saleqty': '19',
                    'fastoreqty': '32'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.42',
                    'qtyrem': '0',
                    'retailstoreqty': '25',
                    'fastorageqty': '575',
                    'sql2': '.02',
                    'fwd': '288',
                    'strate': '.03',
                    'docn': '9',
                    'productname': '177110092',
                    'totqty': '708',
                    'priceactual': '236',
                    'saleqty': '17',
                    'fastoreqty': '59'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.46',
                    'qtyrem': '0',
                    'retailstoreqty': '18',
                    'fastorageqty': '311',
                    'sql2': '0',
                    'fwd': '0',
                    'strate': '.05',
                    'docn': '10',
                    'productname': '177510711',
                    'totqty': '0',
                    'priceactual': '236',
                    'saleqty': '17',
                    'fastoreqty': '39'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.37',
                    'qtyrem': '0',
                    'retailstoreqty': '21',
                    'fastorageqty': '683',
                    'sql2': '.02',
                    'fwd': '780',
                    'strate': '.02',
                    'docn': '11',
                    'productname': '177110008',
                    'totqty': '780',
                    'priceactual': '235',
                    'saleqty': '16',
                    'fastoreqty': '57'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.3',
                    'qtyrem': '0',
                    'retailstoreqty': '19',
                    'fastorageqty': '871',
                    'sql2': '.02',
                    'fwd': '180',
                    'strate': '.02',
                    'docn': '12',
                    'productname': '177110027',
                    'totqty': '960',
                    'priceactual': '233',
                    'saleqty': '16',
                    'fastoreqty': '64'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.46',
                    'qtyrem': '0',
                    'retailstoreqty': '27',
                    'fastorageqty': '196',
                    'sql2': '.04',
                    'fwd': '180',
                    'strate': '.07',
                    'docn': '13',
                    'productname': '177110097',
                    'totqty': '360',
                    'priceactual': '230',
                    'saleqty': '15',
                    'fastoreqty': '59'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.28',
                    'qtyrem': '0',
                    'retailstoreqty': '19',
                    'fastorageqty': '1589',
                    'sql2': '0',
                    'fwd': '0',
                    'strate': '.01',
                    'docn': '14',
                    'productname': '177512260',
                    'totqty': '0',
                    'priceactual': '234',
                    'saleqty': '15',
                    'fastoreqty': '67'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.32',
                    'qtyrem': '0',
                    'retailstoreqty': '18',
                    'fastorageqty': '667',
                    'sql2': '.02',
                    'fwd': '624',
                    'strate': '.02',
                    'docn': '16',
                    'productname': '177110069',
                    'totqty': '804',
                    'priceactual': '193',
                    'saleqty': '13',
                    'fastoreqty': '57'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.51',
                    'qtyrem': '0',
                    'retailstoreqty': '21',
                    'fastorageqty': '372',
                    'sql2': '.03',
                    'fwd': '480',
                    'strate': '.03',
                    'docn': '15',
                    'productname': '177110020',
                    'totqty': '480',
                    'priceactual': '238',
                    'saleqty': '13',
                    'fastoreqty': '41'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.64',
                    'qtyrem': '0',
                    'retailstoreqty': '9',
                    'fastorageqty': '234',
                    'sql2': '0',
                    'fwd': '0',
                    'strate': '.05',
                    'docn': '17',
                    'productname': '377510707',
                    'totqty': '0',
                    'priceactual': '244',
                    'saleqty': '13',
                    'fastoreqty': '14'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.59',
                    'qtyrem': '0',
                    'retailstoreqty': '13',
                    'fastorageqty': '377',
                    'sql2': '.03',
                    'fwd': '480',
                    'strate': '.03',
                    'docn': '18',
                    'productname': '177110119',
                    'totqty': '480',
                    'priceactual': '235',
                    'saleqty': '13',
                    'fastoreqty': '22'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.53',
                    'qtyrem': '0',
                    'retailstoreqty': '16',
                    'fastorageqty': '84',
                    'sql2': '0',
                    'fwd': '0',
                    'strate': '.12',
                    'docn': '20',
                    'productname': '177512265',
                    'totqty': '0',
                    'priceactual': '234',
                    'saleqty': '11',
                    'fastoreqty': '30'
                },
                {
                    'wholesaleqty': '0',
                    'dprate': '.38',
                    'qtyrem': '0',
                    'retailstoreqty': '15',
                    'fastorageqty': '374',
                    'sql2': '.02',
                    'fwd': '480',
                    'strate': '.03',
                    'docn': '19',
                    'productname': '177110088',
                    'totqty': '480',
                    'priceactual': '238',
                    'saleqty': '11',
                    'fastoreqty': '39'
                }
            ]

        };
    },
    props: {
        conent: {
            type: String
        }
    }
};
</script>

<style>
.img-center {
  text-align: center;
}
</style>
