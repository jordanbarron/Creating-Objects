# Creating-Objects
Creating Objects, a better alternative to arrays

package jordan.dev.com.flickr_viewer;

import android.support.v7.app.ActionBarActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ArrayAdapter;
import android.widget.ImageView;
import android.widget.ListView;
import android.widget.TextView;

import java.util.ArrayList;
import java.util.List;


public class ActivityLocation extends ActionBarActivity {

    private ListView listLocations;

    private List<TopLocationObject> TopLocations;





    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_activity_location);

        listLocations = (ListView)findViewById(R.id.listLocations);


        TopLocations = new ArrayList<TopLocationObject>();


        TopLocations.add(new TopLocationObject("Hong Kong",
                "China", R.drawable.china));
        TopLocations.add(new TopLocationObject("Bath",
                "England", R.drawable.united_kingdom));
        TopLocations.add(new TopLocationObject("Bridgetown",
                "Barbados", R.drawable.barbados));
        TopLocations.add(new TopLocationObject("Brussels",
                "Belgium", R.drawable.belgium));
        TopLocations.add(new TopLocationObject("Sydney",
                "Australia", R.drawable.australia));
        TopLocations.add(new TopLocationObject("Sao Paulo",
                "Brazil", R.drawable.brazil));
        TopLocations.add(new TopLocationObject("Havana",
                "Cuba", R.drawable.cuba));
        TopLocations.add(new TopLocationObject("Kingston",
                "Jamaica", R.drawable.jamaica));
        TopLocations.add(new TopLocationObject("Tokyo",
                "Japan", R.drawable.japan));
        TopLocations.add(new TopLocationObject("Riga",
                "Latvia", R.drawable.latvia));

        LocationAdapter adapter = new LocationAdapter(TopLocations);


        listLocations.setAdapter(adapter);


    }


    private class LocationAdapter extends ArrayAdapter<TopLocationObject> {

        public LocationAdapter(List<TopLocationObject> items) {
            super(ActivityLocation.this, 0, items);
        }

        @Override
        public View getView(int position, View convertView, ViewGroup parent) {

            if (convertView == null) {
                convertView = getLayoutInflater().inflate(
                        R.layout.layout, null);
            }

            TextView lblCityName = (TextView)convertView.findViewById(R.id.lblCityName);
            TextView lblCountry = (TextView)convertView.findViewById(R.id.lblCountry);
            ImageView imgflags = (ImageView)convertView.findViewById(R.id.imgFlag);


            TopLocationObject item = TopLocations.get(position);

            lblCityName.setText(item.getCityName());
            lblCountry.setText(item.getCountryName());
            imgflags.setImageResource(item.getFlagResource());



            return convertView;
        }// end get view

    }// end adapter class


}

