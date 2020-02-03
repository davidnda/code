## Building code to generate the correct JSON for a class

````java
        try {
            order = new AmendableOrder();
            Catalog catalog = new Catalog();
            catalog.setId("ABCDEF");
            Specification specification = new Specification();
            List<Feature> featureList = new ArrayList<Feature>();
            Feature feature = new Feature();
            feature = Feature.from("BHIAB","ADDED","HOOD INSULATOR","HOOD INSULATOR",false);
            featureList.add(feature);
            feature = Feature.from("HLHAB","INCLUDED","Rear Parking Sensors","REVERSE PROXIMITY SENSOR*DSN A",false);
            featureList.add(feature);
            specification.setFeatures(featureList);
            specification.setCatalog(catalog);
            MPV mpv= new MPV();
            mpv.setCode("ACMAA_BS-VG_DGADE_DR--C_EN-M1_TR-EW_VS-C1");
            mpv.setState("ADDED");
            specification.setMpv(mpv);
            specification.setRequiredCount(1);
            specification.setPtvl("CR6");
            order.setSpecification(specification);
            OrderReference orderReference = new OrderReference();
            orderReference.setLanguage("E");
            orderReference.setTimestamp("02-02-2020:02:20:20");
            orderReference.setVistaReference("62277918");
            orderReference.setVistaMarket("UB");

            order.setOrderReference(orderReference);
            System.out.println("Order Ref is"+ orderReference.getReference());

            CommercialData commercialData = new CommercialData();
            List<CommercialDataItem> commercialDataItemList = new ArrayList<CommercialDataItem>();
            //CommercialDataItem commercialDataItem = new CommercialDataItem("KEY1","CommDataValue1");
            commercialDataItemList.add(new CommercialDataItem("KEY1","CommDataValue1"));
            commercialDataItemList.add(new CommercialDataItem("KEY2","CommDataValue2"));
            commercialData.setCommercialDataItems(commercialDataItemList);


            order.setCommercialData(commercialData);
            System.out.println("Commercial data looks like "+ commercialDataItemList.get(0).getValue());
            System.out.println("Commercial data looks like "+ commercialDataItemList.get(1).getValue());

            System.out.println("NEW AMENDABLE ORDER AS JSON -- "+order.asJson());
        } catch (JsonProcessingException e) {
            e.printStackTrace();
        }
        
        `
````
